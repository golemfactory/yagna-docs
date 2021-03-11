---
description: Development and deployment of a New Golem network requestor agent
---

# How does it work? A more in-depth look at an example requestor agent

How can I run my tasks over the New Golem network?

In order to run your own payload over the New Golem network, you need to write a requestor agent suited to the work you'd like to have executed by the network's providers.

In this tutorial, we'll show you how to do that.

There are a couple of assumptions we'll be making here, in order to do this tutorial:

* Your task is easily splittable and follows a simple map-reduce model in which the input for the whole task is known beforehand, and the result is constructed directly from the singular outputs produced from each subset of the input. In other words,  the input of each split task does not depend on an output of another split task. 
* Your payload can be executed inside an isolated container and doesn't - by itself - need to access the outside world. **This is a temporary limitation** and we intend to support network connectivity in near future.

## Prerequisites

To proceed with this tutorial, you'll first need to ensure the following prerequisites are met:

* You have the `yagna` daemon running - this is the main service of the new Golem that's responsible for keeping connections with all the other nodes in the network. It exposes its REST API to allow both the provider and the requestor agents to connect to it.
* You have the `yagna` app key generated and noted down so you can use it while running the requestor agent.
* You have the `gftp` binary used to transport files over the New Golem network
* You have your docker image prepared using our `gvmkit` - a tool that converts a docker image to an optimized format better suited for distribution over the New Golem network. This tutorial uses an already converted image containing the Blender renderer which we'll be using to run our tasks, so you can skip this step for now. For details on how to do that with any Docker images, please have a look at this tutorial:  [How to convert a Docker image into a Golem image?](convert-a-docker-image-into-a-golem-image.md)

{% hint style="info" %}
If you are JS developer, please click to **NodeJS**
{% endhint %}

{% tabs %}
{% tab title="Python" %}
* You have `python` &gt;= 3.6 installed and a virtual environment created. You need this to run our example here.
* As we'll be using the Blender renderer in this tutorial, you'll need a Blender scene file that the "providers" will render for you. We have provided an example scene - `cubes.blend` in the example's directory.
* Finally, some familiarity with `asyncio` is a plus, as `yapapi` is written to make heavy use of Python's `asyncio` library.
{% endtab %}

{% tab title="NodeJS" %}
* You have [`nodejs`](https://nodejs.org/en/) &gt;= 12.18.4 and [`yarn`](https://classic.yarnpkg.com/en/docs/install/) &gt;=1.22.3 installed. You need them to run our example here.
* As we'll be using the Blender renderer in this tutorial, you'll need a Blender scene file that the "providers" will render for you. We have provided an example scene - `cubes.blend` in the example's directory.
* Finally, some familiarity with [`generators`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) is a plus, as `yajapi` is written to make heavy use of Generator concept.
{% endtab %}
{% endtabs %}

## Requestor agent code

The complete code of the requestor agent \(no worries, you do not need to copy and paste it as it is already in repo\) is:

{% tabs %}
{% tab title="Python" %}
```python
import asyncio
from datetime import datetime, timedelta
import pathlib
import sys

from yapapi import (
    Executor,
    NoPaymentAccountError,
    Task,
    __version__ as yapapi_version,
    WorkContext,
    windows_event_loop_fix,
)
from yapapi.log import enable_default_logger, log_summary, log_event_repr  # noqa
from yapapi.package import vm
from yapapi.rest.activity import BatchTimeoutError


async def main(subnet_tag, driver=None, network=None):
    package = await vm.repo(
        image_hash="9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
        min_mem_gib=0.5,
        min_storage_gib=2.0,
    )

    async def worker(ctx: WorkContext, tasks):
        script_dir = pathlib.Path(__file__).resolve().parent
        scene_path = str(script_dir / "cubes.blend")
        ctx.send_file(scene_path, "/golem/resource/scene.blend")
        async for task in tasks:
            frame = task.data
            crops = [{"outfilebasename": "out", "borders_x": [0.0, 1.0], "borders_y": [0.0, 1.0]}]
            ctx.send_json(
                "/golem/work/params.json",
                {
                    "scene_file": "/golem/resource/scene.blend",
                    "resolution": (400, 300),
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
            output_file = f"output_{frame}.png"
            ctx.download_file(f"/golem/output/out{frame:04d}.png", output_file)
            try:
                # Set timeout for executing the script on the provider. Two minutes is plenty
                # of time for computing a single frame, for other tasks it may be not enough.
                # If the timeout is exceeded, this worker instance will be shut down and all
                # remaining tasks, including the current one, will be computed by other providers.
                yield ctx.commit(timeout=timedelta(seconds=120))
                # TODO: Check if job results are valid
                # and reject by: task.reject_task(reason = 'invalid file')
                task.accept_result(result=output_file)
            except BatchTimeoutError:
                print(
                    f"Task {task} timed out on {ctx.provider_name}, time: {task.running_time}"
                )
                raise

    # Iterator over the frame indices that we want to render
    frames: range = range(0, 60, 10)
    # Worst-case overhead, in minutes, for initialization (negotiation, file transfer etc.)
    # TODO: make this dynamic, e.g. depending on the size of files to transfer
    init_overhead = 3
    # Providers will not accept work if the timeout is outside of the [5 min, 30min] range.
    # We increase the lower bound to 6 min to account for the time needed for our demand to
    # reach the providers.
    min_timeout, max_timeout = 6, 30

    timeout = timedelta(minutes=max(min(init_overhead + len(frames) * 2, max_timeout), min_timeout))

    # By passing `event_consumer=log_summary()` we enable summary logging.
    # See the documentation of the `yapapi.log` module on how to set
    # the level of detail and format of the logged information.
    async with Executor(
        package=package,
        max_workers=3,
        budget=10.0,
        timeout=timeout,
        subnet_tag=subnet_tag,
        driver=driver,
        network=network,
        event_consumer=log_summary(log_event_repr),
    ) as executor:

        sys.stderr.write(
            f"yapapi version: {yapapi_version}\n"
            f"Using subnet: {subnet_tag}, "
            f"payment driver: {executor.driver}, "
            f"and network: {executor.network}\n"
        )

        num_tasks = 0
        start_time = datetime.now()

        async for task in executor.submit(worker, [Task(data=frame) for frame in frames]):
            num_tasks += 1
            print(
                f"Task computed: {task}, result: {task.result}, time: {task.running_time}"
            )

        print(
            f"{num_tasks} tasks computed, total time: {datetime.now() - start_time}"
        )


if __name__ == "__main__":
    # This is only required when running on Windows with Python prior to 3.8:
    windows_event_loop_fix()

    enable_default_logger()

    loop = asyncio.get_event_loop()
    task = loop.create_task(
        main(subnet_tag="devnet-beta.1", driver="zksync", network="rinkeby")
    )

    try:
        loop.run_until_complete(task)
    except NoPaymentAccountError as e:
        handbook_url = (
            "https://handbook.golem.network/requestor-tutorials/"
            "flash-tutorial-of-requestor-development"
        )
        print(
            f"No payment account initialized for driver `{e.required_driver}` "
            f"and network `{e.required_network}`.\n\n"
            f"See {handbook_url} on how to initialize payment accounts for a requestor node."
        )
    except KeyboardInterrupt:
        print(
            "Shutting down gracefully, please wait a short while "
            "or press Ctrl+C to exit immediately..."
        )
        task.cancel()
        try:
            loop.run_until_complete(task)
            print(
                f"Shutdown completed, thank you for waiting!"
            )
        except (asyncio.CancelledError, KeyboardInterrupt):
            pass

```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
import path from "path";
import dayjs from "dayjs";
import duration from "dayjs/plugin/duration";
import { Executor, Task, utils, vm, WorkContext } from "yajsapi";
import { program } from "commander";

dayjs.extend(duration);

const { asyncWith, logUtils, range } = utils;

async function main() {
  const _package = await vm.repo({
    image_hash: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
    min_mem_gib: 0.5,
    min_storage_gib: 2.0,
  });

  async function* worker(ctx: WorkContext, tasks) {
    ctx.send_file(
      path.join(__dirname, "./cubes.blend"),
      "/golem/resource/scene.blend"
    );

    for await (let task of tasks) {
      let frame: any = task.data();
      let crops = [
        {
          outfilebasename: "out",
          borders_x: [0.0, 1.0],
          borders_y: [0.0, 1.0],
        },
      ];
      ctx.send_json("/golem/work/params.json", {
        scene_file: "/golem/resource/scene.blend",
        resolution: [400, 300],
        use_compositing: false,
        crops: crops,
        samples: 100,
        frames: [frame],
        output_format: "PNG",
        RESOURCES_DIR: "/golem/resources",
        WORK_DIR: "/golem/work",
        OUTPUT_DIR: "/golem/output",
      });
      ctx.run("/golem/entrypoints/run-blender.sh");
      const output_file = `output_${frame.toString()}.png`;
      ctx.download_file(
        `/golem/output/out${frame.toString().padStart(4, "0")}.png`,
        path.join(__dirname, `./output_${frame}.png`)
      );
      yield ctx.commit({timeout: dayjs.duration({ seconds: 120 }).asMilliseconds()});
      // TODO: Check
      // job results are valid // and reject by:
      // task.reject_task(msg = 'invalid file')
      task.accept_result(output_file);
    }

    ctx.log("no more frames to render");
    return;
  }

  const frames: any[] = range(0, 60, 10);
  const timeout: number = dayjs.duration({ minutes: 15 }).asMilliseconds();

  await asyncWith(
    new Executor({
      task_package: _package,
      max_workers: 6,
      timeout: timeout,
      budget: "10.0",
      subnet_tag: "devnet-beta.1",
      driver: "zksync",
      network: "rinkeby",
      event_consumer: logUtils.logSummary(),
    }),
    async (executor: Executor): Promise<void> => {
      for await (let task of executor.submit(
        worker,
        frames.map((frame) => new Task(frame))
      )) {
        console.log("result=", task.result());
      }
    }
  );
  return;
}

main()
```
{% endtab %}
{% endtabs %}

Now to the question:

### How does it work?

Here's the flow diagram of all the interactions that need to happen between the requestor and the provider\(s\) in order for the task to be completed:

![requestor agent - sequential diagram](../.gitbook/assets/requestor-tutorial-sequence.png)

Having learned what is _about_ to happen, let's examine the code itself.

All right, we'll skip over the imports at the top and boilerplate code at the bottom of the example and we'll jump straight into the body of the `main()` routine.

### Specify your demand

Normally, you'd need to adapt your docker image to Golem using the [gvmkit-build](https://pypi.org/project/gvmkit-build/) tool \_\*\*\_but for the purpose of this tutorial, we're using the pre-converted image containing the Blender renderer.

So, first, we need to specify which image we'll be using and what its memory and disk space requirements are:

{% tabs %}
{% tab title="Python" %}
```python
package = await vm.repo(
    image_hash="9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
    min_mem_gib=0.5,
    min_storage_gib=2.0,
)
```
{% endtab %}

{% tab title="NodeJS" %}
```typescript
let _package = await vm.repo(
  "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
  0.5,
  2.0
);
```
{% endtab %}
{% endtabs %}

As you can see, we're pointing to an image within our GVM repository using the hash of the Blender image and we're indicating that it requires half a gigabyte of RAM and 2 gigabytes of disk space.

This effectively creates a `Demand` for the market to respond to. In other words, it communicates to the market that our requestor wants to have the specified image executed with at least the specified amounts of RAM and disk space.

### Define your task's steps

After you have specified the image to run, you need to define the steps that need to be executed by the providers in order to perform your task successfully.

Our high-level API abstracts the minute details of the operations that need to take place between the requestor agent and the providers' end during the execution of the task and its fragments. It also provides a convenient way to specify the needed steps in a routine that is to be performed for each provider, which executes the task fragments assigned to it.

We'll now take the `worker` routine apart, to understand what's happening:

{% tabs %}
{% tab title="Python" %}
```python
async def worker(ctx: WorkContext, tasks):
```
{% endtab %}

{% tab title="NodeJS" %}
```typescript
async function* worker(ctx: WorkContext, tasks) {
```
{% endtab %}
{% endtabs %}

The routine is called with a `ctx` object that contains the work context for a single provider who executes the fragments of the task assigned to them.

`tasks` is a generator that provides tasks from a common queue in an asynchronous way, so that each provider can take another task from the queue as soon as they finish the previous one. The execution continues for as long as there are tasks in the queue.

In this example, we're using a single scene file which all task fragments use, so it only needs to be sent and attached to the provider when the container is first deployed on the provider's end:

{% tabs %}
{% tab title="Python" %}
```python
script_dir = pathlib.Path(__file__).resolve().parent
scene_path = str(script_dir / "cubes.blend")
ctx.send_file(scene_path, "/golem/resource/scene.blend")
```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
ctx.send_file(
  path.join(__dirname, "./cubes.blend"),
  "/golem/resource/scene.blend"
);
```
{% endtab %}
{% endtabs %}

The first parameter to `send_file()` here is the local path of the file. The second one is the path within the _container_ on the provider's end, to which this file should be copied once the container is deployed.

Then, there is a sequence of steps that needs to be executed for each of the fragments, that this provider receives wrapped with this asynchronous loop:

{% tabs %}
{% tab title="Python" %}
```python
async for task in tasks:
```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
for await (let task of tasks) {
```
{% endtab %}
{% endtabs %}

The next few lines are very specific to the Blender use case and the vm image we're using to render each piece of the output. There are a lot of parameters that can be defined here, which are mostly irrelevant in the context of a general requestor development tutorial, so we'll just go through what's most important.

{% tabs %}
{% tab title="Python" %}
```python
frame = task.data
crops = [{"outfilebasename": "out", "borders_x": [0.0, 1.0], "borders_y": [0.0, 1.0]}]
ctx.send_json(
    "/golem/work/params.json",
    {
        "scene_file": "/golem/resource/scene.blend",
        "resolution": (400, 300),
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
{% endtab %}

{% tab title="NodeJS" %}
```typescript
let frame = task.data();
ctx.begin();
let crops = [
  {
    outfilebasename: "out",
    borders_x: [0.0, 1.0],
    borders_y: [0.0, 1.0],
  },
];
ctx.send_json("/golem/work/params.json", {
  scene_file: "/golem/resource/scene.blend",
  resolution: [400, 300],
  use_compositing: false,
  crops: crops,
  samples: 100,
  frames: [frame],
  output_format: "PNG",
  RESOURCES_DIR: "/golem/resources",
  WORK_DIR: "/golem/work",
  OUTPUT_DIR: "/golem/output",
});
```
{% endtab %}
{% endtabs %}

For the sake of simplicity, we have decided to render whole frames of the scene so that the output of each task fragment is a single frame and no subsequent merging of pieces of images is required. The output of a whole task then is just a sequence of images, the merging of which into e.g. a movie file is beyond the scope of this tutorial.

Thus, the `crops` parameter \(which can be used to specify a part of a frame\) stays the same between the tasks and what varies is the `frames` parameter that specifies the frame range to render within each task fragment.

We're using `ctx.send_json()` to wrap the provided dictionary of parameters into a JSON file, the destination path of which is passed as the first parameter. Note that this destination path is again a location within the container that's executed on the provider's end.

As you can see, the `frame` parameter comes from the `data` field of the `Task` objects that are passed into the `Executor`'s `submit` function later on in the code. We could have just as well filled the `data` with e.g. a dictionary containing crop parameters for each fragment - if we wanted to render different parts of images on each fragment's execution. Or we could fill it with names of different scene files, if e.g. we wanted each task to render a completely different scene file. Of course, in this latter case, we'd also need to use `ctx.send_file()` to send a new scene file for each new task fragment.

**TLDR**, the most important take-away here is that `send_json` provides an easy way to pass a dictionary of parameters into the execution container, and that you pass parameters for each task fragment in the `data` field of the `Task` objects passed to the `submit` function.

Okay, next we have the most important step:

{% tabs %}
{% tab title="Python" %}
```python
ctx.run("/golem/entrypoints/run-blender.sh")
```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
ctx.run("/golem/entrypoints/run-blender.sh");
```
{% endtab %}
{% endtabs %}

Which, of course, causes a specific `run` command to be executed by the Docker container on the provider's end. Again, in this case, this script is pretty specific to the use case at hand, and knows that it needs to take the `params.json` file and use it to call Blender in such a way as to render the desired content.

Still, you could just as well run any other command in the container's shell, by also providing its arguments as subsequent parameters to the `run()` function.

After the command finishes its execution, it's time to pass the results back to the requestor:

{% tabs %}
{% tab title="Python" %}
```python
output_file = f"output_{frame}.png"
ctx.download_file(f"/golem/output/out{frame:04d}.png", output_file)
```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
ctx.download_file(
  `/golem/output/out${frame.toString().padStart(4, '0')}.png`,
  path.join(__dirname, `./output_${frame}.png`)
);
```
{% endtab %}
{% endtabs %}

The first parameter here is the source path - which refers to a path within the container on the provider's end - and the second one is the local path on the requestor machine to which the output should be written.

Finally - or _almost_ finally - we issue a `commit()` call which combines all the steps together and we pass them using `yield` to the `Executor.` The Executor, in turn, passes them for execution and allows the flows for other providers to progress on the requestor while this provider works on this task fragment.

Eventually, when the execution returns to our routine and to the work context of the specific provider, we should already have the results available in the desired location.

Ordinarily, you'd most likely want to run some verification of the result to make sure that the provider has done a proper job. Here, for simplicity's sake, we'll just accept the task as it is.

In Python, the `ctx.commit` and `task.accept_result` are wrapped in a try/catch block to handle the timeout of a task on a given provider and handle such timeout gracefully.

{% tabs %}
{% tab title="Python" %}
```python
try:
    # Set timeout for executing the script on the provider. Two minutes is plenty
    # of time for computing a single frame, for other tasks it may be not enough.
    # If the timeout is exceeded, this worker instance will be shut down and all
    # remaining tasks, including the current one, will be computed by other providers.
    yield ctx.commit(timeout=timedelta(seconds=120))
    # TODO: Check if job results are valid
    # and reject by: task.reject_task(reason = 'invalid file')
    task.accept_result(result=output_file)
except BatchTimeoutError:
    print(
        f"Task {task} timed out on {ctx.provider_name}, time: {task.running_time}"
    )
    raise

```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
yield ctx.commit({timeout: dayjs.duration({ seconds: 120 }).asMilliseconds()});
// TODO: Check
// job results are valid // and reject by:
// task.reject_task(msg = 'invalid file')
task.accept_result(output_file);
```
{% endtab %}
{% endtabs %}

And, if the queue is empty and thus the loop is ended, we can finalize the work context of the specific provider.

### Time to call the runner engine

With our task \(fragment\) steps defined, we can finally call the `Executor` , that will orchestrate first the negotiation of our computational `Demand` against the `Offer` from the providers in the network, to reach agreements with each of them and subsequently, will use those agreements to launch specific computational activities to complete the task we have specified. Finally, the Executor will make ensure that payment transactions are triggered for invoices sent from the providers to remunerate them for the work they provided for your task.

The `Executor` is first instantiated as a context manager:

{% tabs %}
{% tab title="Python" %}
```python
frames: range = range(0, 60, 10)
init_overhead = 3
min_timeout, max_timeout = 6, 30

timeout = timedelta(minutes=max(min(init_overhead + len(frames) * 2, max_timeout), min_timeout))

async with Executor(
   package=package,
   max_workers=3,
   budget=10.0,
   timeout=timeout,
   subnet_tag=subnet_tag,
   driver=driver,
   network=network,
   event_consumer=log_summary(),
) as executor:
```
{% endtab %}

{% tab title="NodeJS" %}
```typescript
const frames: any[] = range(0, 60, 10);
const timeout: number = dayjs.duration({ minutes: 15 }).asMilliseconds();

await asyncWith(
  new Executor({
    task_package: _package,
    max_workers: 6,
    timeout: timeout,
    budget: "10.0",
    subnet_tag: "public-beta",
    driver: "zksync",
    network: "rinkeby",
    event_consumer: logUtils.logSummary(),
  }),

```
{% endtab %}
{% endtabs %}

The `package` here is effectively our `Demand` that we have created above, `max_workers` specifies the maximum number of providers we want to be working on our task, `budget` specifies the maximum budget \(in tGLM\) that this task may utilize**,** `timeout` is the time after which we absolutely want our whole task to be finished by and after which we'll treat it as failed unless it's already finished.

The `subnet_tag` serves to select a subset of the network that our requestor node wants to limit its communications to. Using `subnet_tag` we're effectively limiting our list of provider to those that are running with the same `subnet` parameter.

The `driver` and `network` are two new parameters that select the Ethereum network \(`rinkeby` or `mainnet`\) and the payment driver \(`zksync` or `erc20`\) which will be used to pay for the tasks - both of which must be enabled within the yagna daemon.

Finallly, we're providing the consumer of the events that the `Executor` generates with `event_consumer` - our example mostly presents those events to the users in the form of nicely formatted console output but your own app may use in other ways.

With the `Executor` in place, we can finally tell it what we want to execute and also _how_ we want to define each fragment.

{% tabs %}
{% tab title="Python" %}
```python
async for task in executor.submit(worker, [Task(data=frame) for frame in frames]):
    print(f"Task computed: {task}, result: {task.result}")
```
{% endtab %}

{% tab title="NodeJS" %}
```typescript
async (executor: Executor): Promise<void> => {
  for await (let task of executor.submit(
    worker,
    frames.map((frame) => new Task(frame))
  )) {
    console.log("result=", task.result());
  }
}
```
{% endtab %}
{% endtabs %}

As has been mentioned previously, the first parameter to `submit` is the worker routine that defines our task's steps. The second parameter is an iterable defining all the fragments of our whole task that we desire to be executed.

Here we're passing the specific `frame` from the scene that we'd like our Blender container to render. However, it can essentially be any parameter or set of parameters that can accurately describe the job to be executed and it is up for our `worker` routine and - through it - for our containerized payload to make sense of what that set of parameters is.

### YAY!

{% hint style="success" %}
With this, our requestor agent is complete and we can use it to run our computational payload on the New Golem network.
{% endhint %}

## Next steps

Are you hooked up? then go ahead and follow up with our tutorial on using your own - or generally any other - Docker image and using our `gvmkit-builder` tool to build and push the image to our repository:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}

