---
description: Development and deployment of a New Golem network requestor agent
---

# How does it work? A more in-depth look at an example requestor agent

## How can I run my tasks over the New Golem network?

In order to run your own payload over the New Golem network, you need to write a requestor agent suited to the work you'd like to have executed by the network's providers.

In this tutorial, we'll show you how to do that.

There are a couple of assumptions we'll be making here, in order to do this tutorial:

* Your task is easily splittable and follows a simple map-reduce model in which the input for the whole task is known beforehand, and the result is constructed directly from the singular outputs produced from each subset of the input. In other words,  the input of each split task does not depend on an output of another split task. 
* Your payload can be executed inside an isolated container and doesn't - by itself - need to access the outside world. **This is a temporary limitation of this Alpha release** and we intend to support network connectivity in the future.

## Prerequisites

To proceed with this tutorial, you'll first need to ensure the following prerequisites are met:

* You have the `yagna` daemon running - this is the main service of the new Golem that's responsible for keeping connections with all the other nodes in the network. It exposes its REST API to allow both the provider and the requestor agents to connect to it.
* You have the `yagna` app key generated and noted down so you can use it while running the requestor agent.
* You have the `gftp` binary used to transport files over the New Golem network
* You have your docker image prepared using our `gvmkit` - a tool that converts a docker image to an optimized format better suited for distribution over the New Golem network. This tutorial uses an already converted image containing the Blender renderer which we'll be using to run our tasks, so you can skip this step for now. For details on how to do that with any Docker images, please have a look at this tutorial:  __[_How to convert a Docker image into a Golem image_](convert-a-docker-image-into-a-golem-image.md)\_\_
* You have `python` &gt;= 3.6 installed and a virtual environment created. You need this to run our example here.
* As we'll be using the Blender renderer in this tutorial, you'll need a Blender scene file that the "providers" will render for you. We have provided an example scene - `cubes.blend` in the example's directory.
* Finally, some familiarity with `asyncio` is a plus, as `yapapi` is written to make heavy use of Python's `asyncio` library.

## Requestor agent code

The complete code of the requestor agent \(no worries, you do not need to copy and paste it as it is already in repo\) is:

```python
from yapapi.runner import Engine, Task, vm
from yapapi.runner.ctx import WorkContext
from datetime import timedelta
import asyncio


async def main():
    package = await vm.repo(
        image_hash="9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
        min_mem_gib=0.5,
        min_storage_gib=2.0,
    )

    async def worker(ctx: WorkContext, tasks):
        ctx.send_file("./cubes.blend", "/golem/resource/scene.blend")
        async for task in tasks:
            frame = task.data
            ctx.begin()
            crops = [{"outfilebasename": "out", "borders_x": [0.0, 1.0], "borders_y": [0.0, 1.0]}]
            ctx.send_json(
                "/golem/work/params.json",
                {
                    "scene_file": "/golem/resource/scene.blend",
                    "resolution": (800, 600),
                    "use_compositing": False,
                    "crops": crops,
                    "samples": 100,
                    "frames": [frame],
                    "output_format": "PNG",
                    "RESOURCES_DIR": "/golem/resources",
                    "WORK_DIR": "/golem/work",
                    "OUTPUT_DIR": "/golem/output",
                },
            )
            ctx.run("/golem/entrypoints/run-blender.sh")
            ctx.download_file(f"/golem/output/out{frame:04d}.png", f"output_{frame}.png")
            yield ctx.commit()
            # TODO: Check if job results are valid
            # and reject by: task.reject_task(msg = 'invalid file')
            task.accept_task()

        ctx.log("no more frames to render")

    # iterator over the frame indices that we want to render
    frames: range = range(0, 60, 10)
    # TODO make this dynamic, e.g. depending on the size of files to transfer
    # worst-case time overhead for initialization, e.g. negotiation, file transfer etc.
    init_overhead: timedelta = timedelta(minutes=3)

    async with Engine(
        package=package,
        max_workers=10,
        budget=10.0,
        timeout=init_overhead + timedelta(minutes=len(frames) * 2),
        subnet_tag="testnet",
    ) as engine:

        async for progress in engine.map(worker, [Task(data=frame) for frame in frames]):
            print("progress=", progress)


if __name__ == "__main__":
    loop = asyncio.get_event_loop()
    task = loop.create_task(main())
    try:
        asyncio.get_event_loop().run_until_complete(task)
    except (Exception, KeyboardInterrupt) as e:
        print(e)
        task.cancel()
        asyncio.get_event_loop().run_until_complete(asyncio.sleep(0.3))
```

Now to the question:

### How does it work?

Here's the flow diagram of all the interactions that need to happen between the requestor and the provider\(s\) in order for the task to be completed:

![requestor agent - sequential diagram](../.gitbook/assets/requestor-tutorial-sequence.png)

Having learned what is _about_ to happen, let's examine the code itself.

All right, we'll skip over the imports at the top and `asyncio` boilerplate code at the bottom of the example and we'll jump straight into the body of the `main()` routine.

### Specify your demand

Normally, you'd need to adapt your docker image to Golem using the [gvmkit-build](https://pypi.org/project/gvmkit-build/) tool ****but for the purpose of this tutorial, we're using the pre-converted image containing the Blender renderer.

So, first, we need to specify which image we'll be using and what its memory and disk space requirements are:

```python
package = await vm.repo(
    image_hash="9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
    min_mem_gib=0.5,
    min_storage_gib=2.0,
)
```

As you can see, we're pointing to an image within our GVM repository using the hash of the Blender image and we're indicating that it requires half a gigabyte of RAM and 2 gigabytes of disk space.

This effectively creates a `Demand` for the market to respond to. In other words, it communicates to the market that our requestor wants to have the specified image executed with at least the specified amounts of RAM and disk space. 

### Define your task's steps

After you have specified the image to run, you need to define the steps that need to be executed by the providers in order to perform your task successfully.

Our high-level API abstracts the minute details of the operations that need to take place between the requestor agent and the providers' end during the execution of the task. It fragments and provides a convenient way to specify the needed steps in a routine that is to be performed for each provider, which executes the task fragments assigned to it.

We'll now take the `worker` routine apart, to understand what's happening:

```python
async def worker(ctx: WorkContext, tasks):
```

The routine is called with a `ctx` object that contains the work context for a single provider who executes the fragments of the task assigned to them. 

`tasks` is a generator that provides tasks from a common queue in an asynchronous way, so that each provider can take another task from the queue as soon as they finish the previous one. The execution continues for as long as there are tasks in the queue.

In this example, we're using a single scene file which all task fragments use, so it only needs to be sent and attached to the provider when the container is first deployed on the  provider's end:

```python
ctx.send_file("./cubes.blend", "/golem/resource/scene.blend")
```

 The first parameter to `send_file()` here is the local path of the file. The second one is the path within the _container_ on the provider's end, to which this file should be copied once the container is deployed.

Then, there is a sequence of steps that needs to be executed for each of the fragments, that this provider receives wrapped with this asynchronous loop:

```python
async for task in tasks:
```

The next few lines are very specific to the Blender use case and the vm image we're using to render each piece of the output. There are a lot of parameters that can be defined here, which are mostly irrelevant in the context of a general requestor development tutorial, so we'll just go through what's most important.

```python
frame = task.data
ctx.begin()
crops = [{"outfilebasename": "out", "borders_x": [0.0, 1.0], "borders_y": [0.0, 1.0]}]
ctx.send_json(
    "/golem/work/params.json",
    {
        "scene_file": "/golem/resource/scene.blend",
        "resolution": (800, 600),
        "use_compositing": False,
        "crops": crops,
        "samples": 100,
        "frames": [frame],
        "output_format": "PNG",
        "RESOURCES_DIR": "/golem/resources",
        "WORK_DIR": "/golem/work",
        "OUTPUT_DIR": "/golem/output",
    },
)
```

For the sake of simplicity, we have decided to render whole frames of the scene so that the output of each task fragment is a single frame and no subsequent merging of pieces of images is required. The output of a whole task then is just a sequence of images, the merging of which into e.g. a movie file is beyond the scope of this tutorial.

Thus, the `crops` parameter \(which can be used to specify a part of a frame\) stays the same between the tasks and what varies is the `frames` parameter that specifies the frame range to render within each task fragment.

We're using `ctx.begin()` to start the sequence of commands for this specific fragment,  then`ctx.send_json()` to wrap the provided dictionary of parameters into a JSON file, the destination path of which is passed as the first parameter. Note that this destination path is again a location within the container that's executed on the provider's end.

As you can see, the `frame` parameter comes from the `data` field of the `Task` objects that are passed into the `Engine`'s `map` function later on in the code. We could have just as well filled the `data` with e.g. a dictionary containing crop parameters for each fragment - if we wanted to render different parts of images on each fragment's execution. Or we could fill it with names of different scene files, if e.g. we wanted each task to render a completely different scene file. Of course, in this latter case, we'd also need to use `ctx.send_file()` to send a new scene file for each new task fragment.

**TLDR**, the most important take-away here is that `send_json` provides an easy way to pass a dictionary of parameters into the execution container, and that you pass parameters for each task fragment in the `data` field of the `Task` objects passed to the `map` function. 

Okay, next we have the most important step:

```python
ctx.run("/golem/entrypoints/run-blender.sh")
```

Which, of course, causes a specific `run` command to be executed by the Docker container on the provider's end. Again, in this case, this script is pretty specific to the use case at hand, and knows that it needs to take the `params.json` file and use it to call `Blender` in such a way as to render the desired content.

Still, you could just as well run any other command in the container's shell, by also providing its arguments as subsequent parameters to the `run()` function.

After the command finishes its execution, it's time to pass the results back to the requestor:

```python
ctx.download_file(f"/golem/output/out{frame:04d}.png", f"output_{frame}.png")
```

The first parameter here is the source path - which refers to a path within the container on the provider's end - and the second one is the local path on the requestor machine to which the output should be written.

Finally - or _almost_ finally - we issue a `commit()` call which combines all the steps together and we pass them using `yield` to the `Engine.` The Engine, in turn, passes them for execution and allows the flows for other providers to be executed on the requestor while this provider works on this task fragment.

```python
yield ctx.commit()
```

Eventually, when the execution returns to our routine and to the work context of the specific provider, we should already have the results available in the desired location.

Ordinarily, you'd most likely want to run some verification of the result to make sure that the provider has done a proper job. Here, for simplicity's sake, we'll just accept the task as it is.

```python
task.accept_task()
```

And, if the queue is empty and thus the loop is ended, we can finalize the work context of the specific provider - here, just by stating that we see no more frames to render.

```python
ctx.log("no more frames to render")
```

### Time to call the runner Engine

With our task \(fragment\) steps defined, we can finally call the `Engine` , that will orchestrate first the negotiation of our computational `Demand` against the `Offer` from the providers in the network, to reach agreements with each of them and subsequently, will use those agreements to launch specific computational activities to complete the task we have specified. **\[ WHAT ABOUT THE PAYMENTS? \]**

The `Engine` is first instantiated as a context manager:

```python
    frames: range = range(0, 60, 10)
    init_overhead: timedelta = timedelta(minutes=3)

    async with Engine(
        package=package,
        max_workers=10,
        budget=10.0,
        timeout=init_overhead + timedelta(minutes=len(frames) * 2),
        subnet_tag="testnet",
    ) as engine:
```

The `package` here is effectively our `Demand` that we have created above. `max_workers` specifies the maximum number of providers we want to be working on our task, `budget` specifies the maximum budget \(in nGNT\) that this task may utilize**,** `timeout` is the time after which we absolutely want our whole task to be finished by and after which we'll treat it as failed unless it's already finished. Finally, the `subnet_tag` serves to select a subset of the network that our requestor node wants to limit its communications to.

The last parameter means that if we do specify the subnet - each and every provider who wants to execute our tasks must be running with the same `subnet` parameter. 

With the `Engine` in place, we can finally tell it what we want to execute and also _how_ we want to define each fragment.

```python
        async for progress in engine.map(
                worker,
                [Task(data=frame) for frame in frames]
        ):
            print("progress=", progress)
```

As has been mentioned previously, the first parameter to `map` is the worker routine that defines our task's steps. The second parameter is an iterable defining all the fragments of our whole task that we desire to be executed.

Here we're passing the specifIc `frame` from the scene that we'd like our Blender container to render. However,  it can essentially be any parameter or set of parameters that can accurately describe the job to be executed and it is up for our `worker` routine and - through it - for our containerized payload to make sense of what that set of parameters is.

### YAY!

{% hint style="success" %}
With this, our requestor agent is complete and we can use it to run our computational payload on the New Golem network.
{% endhint %}

## Next steps

Are you hooked up? then go ahead and follow up with our tutorial on using your own - or generally any other - Docker image and using our `gvmkit-builder` tool to build and push the image to our repository:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}





