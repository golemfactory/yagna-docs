---
description: A minimal example of a Golem requestor agent based on services
---

# Service Example 0: Hello world?

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Service provisioning and execution
* Retrieving command output from provider's exe unit
{% endhint %}

## Prerequisites

This example shares a number of concepts, as well as parts of its code with the task model "Hello World!". Therefore the below article can be considered a good introduction:

{% page-ref page="../task-processing-development/task-example-0-hello.md" %}

Also, in case you haven't done so already, it's a good idea to take a look at the [Introduction to the service model](service-model-introduction.md) before proceeding.

{% hint style="warning" %}
Please note that as of its current latest version \(`0.4.0`\) the JS high-level API \(`yajsapi`\) does not yet support the service model. Therefore, this article includes only Python code examples.
{% endhint %}

## Requestor agent code

{% tabs %}
{% tab title="Python" %}
```python
#!/usr/bin/env python3
import asyncio
from datetime import datetime, timedelta

from yapapi import Golem
from yapapi.executor.services import Service
from yapapi.log import enable_default_logger
from yapapi.payload import vm

DATE_OUTPUT_PATH = "/golem/work/date.txt"
REFRESH_INTERVAL_SEC = 5


class DateService(Service):
    @staticmethod
    async def get_payload():
        return await vm.repo(
            image_hash="d646d7b93083d817846c2ae5c62c72ca0507782385a2e29291a3d376",
        )

    async def start(self):
        # every `DATE_POLL_INTERVAL` write output of `date` to `DATE_OUTPUT_PATH`
        self._ctx.run(
            "/bin/sh",
            "-c",
            f"while true; do date > {DATE_OUTPUT_PATH}; sleep {REFRESH_INTERVAL_SEC}; done &",
        )
        yield self._ctx.commit()

    async def run(self):
        while True:
            await asyncio.sleep(REFRESH_INTERVAL_SEC)
            self._ctx.run(
                "/bin/sh",
                "-c",
                f"cat {DATE_OUTPUT_PATH}",
            )

            future_results = yield self._ctx.commit()
            results = await future_results
            print(results[0].stdout.strip())


async def main():
    async with Golem(budget=1.0, subnet_tag="devnet-beta.2") as golem:
        cluster = await golem.run_service(DateService, num_instances=1)
        start_time = datetime.now()

        while datetime.now() < start_time + timedelta(minutes=1):
            for num, instance in enumerate(cluster.instances):
                print(f"Instance {num} is {instance.state.value} on {instance.provider_name}")
            await asyncio.sleep(REFRESH_INTERVAL_SEC)


if __name__ == "__main__":
    enable_default_logger(log_file="hello.log")

    loop = asyncio.get_event_loop()
    task = loop.create_task(main())
    loop.run_until_complete(task)

```
{% endtab %}
{% endtabs %}

Besides the usual boilerplate in the form of imports and the entry function there are two crucial pieces to this program:

1. `DateService` class, which is the implementation of our example service. It defines how the service should be started and what action it should perform.
2. `main()` function, which creates an instance of `Golem` to take care of provisioning our service using the Golem network.

Let's now take a closer look at both of the components mentioned above.

## Service implementation

In the Golem API, services are implemented by extending the base `Service` class. By overriding certain methods from that class we can define our service's life cycle, as well as its payload. Here's an overview of this interface:

* `get_payload() -> Optional[Payload]` returns the `Payload` object which describes the execution environment we want our service instances to run on. In the case of the VM runtime this will include a hash of the VM image to be deployed. If we choose not to implement this method our payload will need to be specified when running the service through `Golem.run_service`.
* `start() -> None` called for each service instance when it enters the `starting` state. This should contain the sequence of steps which need to be taken in order for our service to be started.
* `run() -> None` called for each service instance when it enters the `running` state. This is where the main loop of our service should be implemented.
* `shutdown() -> None` called for each service instance when it enters the `stopping` state. In case our service requires some cleanup logic to be run before an instance is terminated, this is where it should be placed.

All three life cycle methods \(i.e. `start`, `run` and `shutdown`\) are optional, although in most cases a service will require at least `start` and `run` to be implemented.

{% hint style="info" %}
To control service instances running on remote exe units, all life cycle methods require access to a `WorkContext` object tied to some active instance.

This `WorkContext` instance is provided through the field `self._ctx` of the `Service` class. This means that, behind the scenes, an object of our `Service` subclass is spawned for each service instance running on a provider.
{% endhint %}

### payload definition

{% tabs %}
{% tab title="Python" %}
```python
@staticmethod
async def get_payload():
    return await vm.repo(
        image_hash="d646d7b93083d817846c2ae5c62c72ca0507782385a2e29291a3d376"
    )
```
{% endtab %}
{% endtabs %}

Our `DateService` uses the same image hash as the [Task Example 0: Hello World!](../task-processing-development/task-example-0-hello.md). This hash points to a pre-uploaded, minimal image based on Alpine Linux.

### start\(\) function

{% tabs %}
{% tab title="Python" %}
```python
async def start(self):
    # every `DATE_POLL_INTERVAL` write output of `date` to `DATE_OUTPUT_PATH`
    self._ctx.run(
        "/bin/sh",
        "-c",
        f"while true; do date > {DATE_OUTPUT_PATH}; sleep {REFRESH_INTERVAL_SEC}; done &",
    )
    yield self._ctx.commit()
```
{% endtab %}
{% endtabs %}

Our `start` function is responsible for starting a background process on the provider's exe unit. In the case of `DateService` this process is going to be the following `bash` command:

{% tabs %}
{% tab title="Bash" %}
```bash
while true; do date > /golem/work/date.txt; sleep 5; done &
```
{% endtab %}
{% endtabs %}

The above command has its placeholders substituted with their actual default values. When run in the provider's exe unit, this will keep rewriting the file `/golem/work/date.txt` with the output of `date` every 5 seconds.

The file `/golem/work/date.txt` will be our source of data which we'll later on read in our service's `run` function.

### run\(\) function

{% tabs %}
{% tab title="Python" %}
```python
async def run(self):
    while True:
        await asyncio.sleep(REFRESH_INTERVAL_SEC)
        self._ctx.run(
            "/bin/sh",
            "-c",
            f"cat {DATE_OUTPUT_PATH}",
        )

        future_results = yield self._ctx.commit()
        results = await future_results
        print(results[0].stdout.strip())
```
{% endtab %}
{% endtabs %}

