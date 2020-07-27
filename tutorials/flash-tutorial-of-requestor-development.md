---
description: Copy and paste quick tutorial
---

# Flash tutorial of requestor development

This is complete creating and running golem requestor tutorial.

The tutorial shows how to create requestor that is doing [Blender](https://www.blender.org/) rendering in parallel in multiple requestors with the use of Blender's docker image. 

TO DO: 

binary instead of cargo

show gvmkit usage

testnet support in python code

### Running `yagna` daemon from sources

To run `yagna` from sources, you'll need to have `rust` development environment installed - it will be needed to run the `yagna` daemon itself. If you don't have it, please refer to the official docs to install it: [https://www.rust-lang.org/learn/get-started](https://www.rust-lang.org/learn/get-started) 

Afterward, you'll need to launch the `yagna` service.

First, clone the `yagna` repository from: [https://github.com/golemfactory/yagna/](https://github.com/golemfactory/yagna/releases/tag/vm-poc)

```python
git clone https://github.com/golemfactory/yagna.git
```

Once you have it cloned and checked out, enter its directory and: first, copy the template environment file onto a proper .env file:

```bash
cp .env-template .env
```

 then run:

```text
cargo run service run
```

This will build the `yagna` using the Rust compiler \(which can take a considerable time unless you're working on a really fast machine\) and subsequently launch it.

Once the daemon launches, it will start emitting some debug messages among which one of the first ones will look like: `[2020-07-16T12:11:33Z INFO yagna] Starting yagna service!` .  There you go! Leave the shell with the yagna service running and you're ready for the following steps.

### Generate the app key

With the daemon running, enter the daemon's directory using another shell and generate the `yagna` app key that will be used by your requestor agent to access yagna's REST API.

```text
cargo run app-key create requestor
```

This should produce a 32-character-long hexadecimal app key that you need to note down as it will be needed to run the requestor agent.

In case you lose your app key, you can retrieve it with:

```text
cargo run app-key list
```

the value in the `key` column is the key you need.

### Build the `gftp` binary

If you're running `yagna` from sources, you won't have the `gftp` binary around and you need to also build it yourself. To do so, once again, go to your `yagna` source directory and execute:

```bash
cd core/gftp
cargo install --path .
```

This will build and install the `gftp` binary for you.

### Ensure you have some ETH and GNT tokens ready

```text
cargo run payment init -r
```

and allow a few minutes for the faucet to do its job.

You can verify whether you already have the funds with:

```text
cargo run payment status
```

If it doesn't succeed after a few minutes, re-run the `payment init` command above and check again after a few more minutes.

## Requestor agent code

The complete code of the requestor agent is:

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

            task.accept_task()

        ctx.log("no more frames to render")

    async with Engine(
        package=package, max_workers=10, budget=10.0, timeout=timedelta(minutes=15), subnet_tag="demo-1"
    ) as engine:

        async for progress in engine.map(worker, [Task(data=frame) for frame in range(0, 60, 10)]):

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

You do not need to copy and paste it as it is allready in repo. The detailed description of how it works is here:

{% page-ref page="requestor-tutorial.md" %}

### YAY!

{% hint style="success" %}
With this, our requestor agent is complete and we can use it to run our computational payload on the new golem network.
{% endhint %}

## Running the requestor

To run the above code:

* prepare virtual environment for the tutorial script, e.g. with `virtualenvwrapper`:

```text
mkvirtualenv -p python3 yagna-python-tutorial
```

* and install the dependencies:

```text
pip install yapapi certifi
```

* copy the above example python requestor code and place it as `example.py` in the same directory as your blender scene file
* if you're using a scene file with a different name than `cubes.blend` above make sure that your example code refers to your scene file
* set the `YAGNA_APPKEY` to the app key that you received after you have created the yagna app key

```text
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

* and run the requestor agent:

```text
python3 ./example.py
```



