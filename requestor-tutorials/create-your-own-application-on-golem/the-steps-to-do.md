---
description: List of actions needed to execute the hashcat example.
---

# Tutorial steps

This section contains steps you need to execute in order to run our hashcat password-recovery example. As this tutorial is designed to inspire you to create your own Golem applications, we will explain all the needed details of Golem application implementation.

## Before we begin

In order to develop applications for the Golem network, you need to install yagna daemon on your machine. We're going to assume you're already familiar with the setup of the environment required to run Python high-level API examples. If you're not, please make sure you proceed through our quick primer to get up to speed:

{% page-ref page="../flash-tutorial-of-requestor-development.md" %}

Once you're done with the tutorial above, make sure you're again in yapapi's main directory and move to:

```text
cd examples/yacat
```

{% hint style="success" %}
So now, we're going to assume that:

* The `yagna` deamon is running in the background. 
* The `YAGNA_APPKEY` environment variable is set to the value of the generated app key.
* The payment is initialized with `yagna payment init -r`  \(please keep in mind that it needs initialization after each launch of `yagna service run`\).
* The virtual python environment for our tutorial is activated.
* Dependencies are installed and the `yapapi` repository \(containing the tutorial examples\) is cloned.
* In your current directory there are two files that will be used and discussed in this example:
  * `yacat.Dockerfile` - the Docker file used for the definition of the provider's container images
  * `yacat.py` - requestor agent's entry point which deals with orchestration of the container runs.
{% endhint %}

## Let's get to work - the Dockerfile

Let's start with the Dockerfile \(`yacat.Dockerfile`\). Do we always need a dedicated Dockerfile for our own Golem application?

{% hint style="info" %}
Golem is designed to use existing Docker images, so you can use any existing docker image. There are no Golem-specific conditions that need to be met by the image.
{% endhint %}

If there is \(for example on the [docker hub](https://hub.docker.com/)\) no docker image that you need, you will have to create a custom one.

For the yacat example we're going to use the following Dockerfile \(`yacat.Dockerfile`\):

```text
FROM golemfactory/base:1.5

MAINTAINER Radek Tereszczuk <radoslaw.tereszczuk@golem.network>

RUN apt-get update && apt-get install -y alien clinfo

# Install Intel OpenCL driver
#ENV INTEL_OPENCL_URL=http://registrationcenter-download.intel.com/akdlm/irc_nas/vcp/13793/l_opencl_p_18.1.0.013.tgz
ENV INTEL_OPENCL_URL=http://registrationcenter-download.intel.com/akdlm/irc_nas/9019/opencl_runtime_16.1.1_x64_ubuntu_6.4.0.25.tgz

RUN mkdir -p /tmp/opencl-driver-intel
WORKDIR /tmp/opencl-driver-intel
RUN curl -O $INTEL_OPENCL_URL; \
    tar -xzf $(basename $INTEL_OPENCL_URL); \
    for i in $(basename $INTEL_OPENCL_URL .tgz)/rpm/*.rpm; do alien --to-deb $i; done; \
    dpkg -i *.deb; \
    mkdir -p /etc/OpenCL/vendors; \
    echo /opt/intel/*/lib64/libintelocl.so > /etc/OpenCL/vendors/intel.icd; \
    rm -rf *

ENV HASHCAT_VERSION        hashcat-5.1.0
ENV HASHCAT_UTILS_VERSION  1.9

# Update & install packages for installing hashcat
RUN apt-get update && \
    apt-get install -y wget p7zip make build-essential git libcurl4-openssl-dev libssl-dev zlib1g-dev

RUN mkdir /golem/yacat

WORKDIR /golem/yacat
RUN wget --no-check-certificate https://hashcat.net/files/${HASHCAT_VERSION}.7z && \
    7zr x ${HASHCAT_VERSION}.7z && \
    rm ${HASHCAT_VERSION}.7z

RUN wget --no-check-certificate https://github.com/hashcat/hashcat-utils/releases/download/v${HASHCAT_UTILS_VERSION}/hashcat-utils-${HASHCAT_UTILS_VERSION}.7z && \
    7zr x hashcat-utils-${HASHCAT_UTILS_VERSION}.7z && \
    rm hashcat-utils-${HASHCAT_UTILS_VERSION}.7z

#Add link for binary
RUN ln -s /golem/yacat/${HASHCAT_VERSION}/hashcat64.bin /usr/bin/hashcat
RUN ln -s /golem/yacat/hashcat-utils-${HASHCAT_UTILS_VERSION}/bin/cap2hccapx.bin /usr/bin/cap2hccapx

RUN cp /golem/yacat/${HASHCAT_VERSION}/hashcat.hcstat2 /golem/yacat
RUN chmod -R 777 /golem/yacat

RUN apt clean

WORKDIR /golem/work

VOLUME /golem/work /golem/output /golem/resource
```

As Golem does not need any specific elements in the Dockerfile,`yacat.Dockerfile`is just a standard Dockerfile. For the requestor agent code, which we are going to discuss in the next chapter, we need to know the volume name. This is the last line of the above Dockerfile:

```text
VOLUME /golem/work /golem/output /golem/resource
```

This makes `/golem/work` a location we will use for our input / output file transfer. We are also defining other volumes for possible future usage.

Now we may proceed with a regular Docker build, using `yacat.Dockerfile`:

```python
docker build . -f yacat.Dockerfile -t yacat
```

As Golem cannot currently use raw docker images and uses its own, optimized `gvmkit` image format, we have to convert our Docker image the following way:

```python
pip install gvmkit-build
gvmkit-build yacat
gvmkit-build yacat --push
```

The important fact is that the last of the above commands, will provide us with a `gvmkit` image hash, that looks like this:

```python
2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9
```

{% hint style="info" %}
This hash will identify our image when our Golem application is run. Please copy and save it somewhere as in the requestor agent code, we will need to pass it to the `Engine` in order to have providers use the correct image for the container instances.
{% endhint %}

The details of docker image conversion are described here:

{% page-ref page="../convert-a-docker-image-into-a-golem-image.md" %}

## The requestor agent code

Let's look at the core of our hashcat example - the requestor agent. Please check the `yacat.py` file below.

{% hint style="info" %}
The critical fragments of `yacat.py` will be described in the following sections of the tutorial so now, you can just do a quick scan over the wall of code below.
{% endhint %}

```python
 #!/usr/bin/env python3
import asyncio
from datetime import timedelta
import pathlib
import sys

from yapapi.log import enable_default_logger, log_summary, log_event_repr  # noqa
from yapapi.runner import Engine, Task, vm
from yapapi.runner.ctx import WorkContext


# For importing `utils.py`:
script_dir = pathlib.Path(__file__).resolve().parent
parent_directory = script_dir.parent
sys.stderr.write(f"Adding {parent_directory} to sys.path.\n")
sys.path.append(str(parent_directory))
import utils  # noqa


def write_hash(hash):
    with open("in.hash", "w") as f:
        f.write(hash)


def write_keyspace_check_script(mask):
    with open("keyspace.sh", "w") as f:
        f.write(f"hashcat --keyspace -a 3 {mask} -m 400 > /golem/work/keyspace.txt")


def read_keyspace():
    with open("keyspace.txt", "r") as f:
        return int(f.readline())


def read_password(ranges):
    for r in ranges:
        with open(f"hashcat_{r}.potfile", "r") as f:
            line = f.readline()
        split_list = line.split(":")
        if len(split_list) >= 2:
            return split_list[1]
    return None


async def main(args):
    package = await vm.repo(
        image_hash="2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9",
        min_mem_gib=0.5,
        min_storage_gib=2.0,
    )

    async def worker_check_keyspace(ctx: WorkContext, tasks):
        async for task in tasks:
            keyspace_sh_filename = "keyspace.sh"
            ctx.send_file(keyspace_sh_filename, "/golem/work/keyspace.sh")
            ctx.run("/bin/sh", "/golem/work/keyspace.sh")
            output_file = "keyspace.txt"
            ctx.download_file("/golem/work/keyspace.txt", output_file)
            yield ctx.commit()
            task.accept_task()

    async def worker_find_password(ctx: WorkContext, tasks):
        ctx.send_file("in.hash", "/golem/work/in.hash")

        async for task in tasks:
            skip = task.data
            limit = skip + step

            # Commands to be run on the provider
            commands = (
                "touch /golem/work/hashcat.potfile; "
                f"hashcat -a 3 -m 400 /golem/work/in.hash --skip {skip} --limit {limit} {args.mask} -o /golem/work/hashcat.potfile"
            )
            ctx.run(f"/bin/sh", "-c", commands)

            output_file = f"hashcat_{skip}.potfile"
            ctx.download_file(f"/golem/work/hashcat.potfile", output_file)
            yield ctx.commit()
            task.accept_task(result=output_file)

    # beginning of the main flow

    write_hash(args.hash)
    write_keyspace_check_script(args.mask)

    # By passing `event_emitter=log_summary()` we enable summary logging.
    # See the documentation of the `yapapi.log` module on how to set
    # the level of detail and format of the logged information.
    async with Engine(
        package=package,
        max_workers=args.number_of_providers,
        budget=10.0,
        # timeout should be keyspace / number of providers dependent
        timeout=timedelta(minutes=25),
        subnet_tag=args.subnet_tag,
        event_emitter=log_summary(log_event_repr),
    ) as engine:

        # this is not typical use of engine.map as, there is only one task, with no data
        async for task in engine.map(worker_check_keyspace, [Task(data=None)]):
            pass

        keyspace = read_keyspace()

        print(
            f"{utils.TEXT_COLOR_CYAN}"
            f"Task computed: keyspace size count. The keyspace size is {keyspace}"
            f"{utils.TEXT_COLOR_DEFAULT}"
        )

        step = int(keyspace / args.number_of_providers) + 1

        ranges = range(0, keyspace, step)

        async for task in engine.map(worker_find_password, [Task(data=range) for range in ranges]):
            print(
                f"{utils.TEXT_COLOR_CYAN}"
                f"Task computed: {task}, result: {task.output}"
                f"{utils.TEXT_COLOR_DEFAULT}"
            )

        password = read_password(ranges)

        if password is None:
            print(f"{utils.TEXT_COLOR_RED}No password found{utils.TEXT_COLOR_DEFAULT}")
        else:
            print(
                f"{utils.TEXT_COLOR_GREEN}"
                f"Password found: {password}"
                f"{utils.TEXT_COLOR_DEFAULT}"
            )


if __name__ == "__main__":
    parser = utils.build_parser("yacat")

    parser.add_argument("--number-of-providers", dest="number_of_providers", type=int, default=3)
    parser.add_argument("mask")
    parser.add_argument("hash")

    args = parser.parse_args()

    enable_default_logger(log_file=args.log_file)

    sys.stderr.write(
        f"Using subnet: {utils.TEXT_COLOR_YELLOW}{args.subnet_tag}{utils.TEXT_COLOR_DEFAULT}\n"
    )

    loop = asyncio.get_event_loop()
    task = loop.create_task(main(args))

    try:
        loop.run_until_complete(task)
    except (Exception, KeyboardInterrupt) as e:
        print(e)
        task.cancel()
        loop.run_until_complete(task)
```

## So what is happening here?

### worker\_check\_keyspace

The first step is to **check the keyspace size**. This is done in 3 steps, executed only once using one task fragment:

1. Preparing the `keyspace.sh` script which contains the password mask. As the `hashcat --keyspace -a 3 {mask} -m 400` command outputs the keyspace size to `stdout`, we just need to redirect the command output to the `keyspace.txt` file. The  `keyspace.sh` then looks like: `hashcat --keyspace -a 3 {mask} -m 400 > /golem/work/keyspace.txt`
2. Execute the `keyspace.sh` script on the provider's container.
3. Transfer the `keyspace.txt` file back to the requestor.

![](../../.gitbook/assets/tutorial-04.jpg)

Knowing the keyspace size, we can start looking for the password using multiple workers, running on multiple providers at the same time.

### worker\_find\_password

In order to look for passwords in the given keyspace range, for each of the workers employed to perform our job, we are executing the following 3 steps:

* Send the `in.hash` file that contains the password hash. 
* Execute`hashcat` with proper `--skip` and `--limit` values
* Get the hashcat.potfile from the provider to the requestor

![](../../.gitbook/assets/tutorial-03.jpg)

### read\_password

The final action is to scan over all the `*.potfiles` received. If there is a password, it will be displayed to the user.

## How does the code work?

### Package

To tell the Golem platform, what our requirements against the providers are, we are using the `package` object. The `image_hash` parameter points to the image that we want the containers to run - here we use the hash received from `gvmkit-build`. The `min_mem_gib` and `min_storage_gib` parameters specify memory and storage requirements for the provider.

```python
 package = await vm.repo(
     image_hash="2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9",
     min_mem_gib=0.5,
     min_storage_gib=2.0,
 )
```

### Engine

The `package` object is passed to the `engine` object with several other options, such as:

* `budget`defines maximal spendings for executing all the tasks in the whole run on Golem
* `max_workers` defines the maximal number of simultaneously running workers \(and that is, the maximum number of providers that the task fragments will be distributed to\).
* `timeout` defines the timeout. It is important for the timeout to be large enough to include the image download time plus the computation time.
* `subnet_tag` specifies the providers subnet to be used. For example, you would not use the mainnet network for tests.

```python
async with Engine(
    package=package,
    max_workers=args.number_of_providers,
    budget=10.0,
    # timeout should be keyspace / number of providers dependent
    timeout=timedelta(minutes=25),
    subnet_tag=args.subnet_tag,
    event_emitter=log_summary(log_event_repr),
) as engine:
```

### Main loop

Golem high-level API that we use to interact with the Golem network uses asynchronous programming a lot. The asynchronous execution starting point is in line 152:

```python
loop = asyncio.get_event_loop()
task = loop.create_task(main(args))

try:
    loop.run_until_complete(task)
except (Exception, KeyboardInterrupt) as e:
    print(e)
    task.cancel()
    loop.run_until_complete(task)
```

In the `main` function, the most important fragment begins in line 100:

```python
async for task in engine.map(worker_check_keyspace, [Task(data=None)]):
    pass
```

This calls the `worker_check_keyspace` once with no additional task parameters. The next step is getting the `keyspace` variable from the `keyspace.txt` file:

```python
keyspace = read_keyspace()
```

Now we can split the whole `keyspace` by the `args.number_of_providers`:

```python
 step = int(keyspace / args.number_of_providers) + 1

 ranges = range(0, keyspace, step)
```

Having the `ranges` list, we can call the `worker_find_password` for each of the fragments, passing only the given `range`:

```python
async for task in engine.map(worker_find_password, [Task(data=range) for range in ranges]):
    print(
        f"{utils.TEXT_COLOR_CYAN}"
        f"Task computed: {task}, result: {task.output}"
        f"{utils.TEXT_COLOR_DEFAULT}"
    )
```

After the `hashcat.potfile` file is returned for all the fragments, we need to scan over them, as one of them possibly contains the password we are looking for:

```python
password = read_password(ranges)
```

### worker\_check\_keyspace

The `worker_check_keyspace` is also interesting. Here we need to execute the following command on only one of the providers:

```python
hashcat --keyspace -a 3 {mask} -m 400
```

As this command is using the `stdout` to display the keyspace size information, we need the `stdout` to be captured.

As we can not use `ctx.run` directly to redirect stdout to `keyspace.txt`, we are preparing `keyspace.sh` file with the following content:`hashcat --keyspace -a 3 {mask} -m 400 > keyspace.txt`.

Next, we're going to send `keyspace.sh` to one of the providers running our image and have them execute a single command:

```python
ctx.run("/bin/sh","/golem/work/keyspace.sh")
```

Now we can transfer the `keyspace.txt` back to the requestor

```python
output_file = "keyspace.txt"
ctx.download_file(f"/golem/work/keyspace.txt", output_file)
```

### worker\_find\_password

This function is executed on each of the providers. First, we are sending them the `in.hash` file that contains the known hash. That needs only to be run once per worker run \(which usually means once per provider\).

```python
ctx.send_file("in.hash", "/golem/work/in.hash")
```

Then, for each task fragment that this worker is executing, we are preparing the `--skip` and `--limit` parameters, and executing the commands on the provider:

```python
skip = task.data
limit = skip + step

# Commands to be run on the provider
commands = (
    "touch /golem/work/hashcat.potfile; "
     f"hashcat -a 3 -m 400 /golem/work/in.hash --skip {skip} --limit {limit} {args.mask} -o /golem/work/hashcat.potfile"
)
ctx.run(f"/bin/sh", "-c", commands)
```

We also need to execute the `touch /golem/work/hashcat.potfile` command in order to have `/golem/work/hashcat.potfile` file present in the file system even if there is no password output by Hashcat.

The last step is downloading the `/golem/work/hashcat.potfile` file.

```python
output_file = f"hashcat_{skip}.potfile"
ctx.download_file(f"/golem/work/hashcat.potfile", output_file)
```

{% hint style="success" %}
Now, as we know how the yacat works, let's run it!
{% endhint %}

## Example run

While in the `/examples/yacat` directory, type the following:

```python
python3 yacat.py '?a?a?a' '$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/' --subnet-tag devnet-alpha.2
```

{% hint style="danger" %}
Please note that on Windows, you need to:

* use `python` instead of `python3`
* not use the quote character in the command

So the windows version is:

```python
python yacat.py ?a?a?a $P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/ --subnet-tag devnet-alpha.2
```
{% endhint %}

The above run should return "pas" as the recovered password. The computations will be executed using the default number of workers \(which is 3\).

A more computation-intensive example is:

```python
python3 yacat.py '?a?a?a?a' '$H$5ZDzPE45C.e3TjJ2Qi58Aaozha6cs30' --subnet-tag devnet-alpha.2 --number-of-providers 8
```

The above command should execute computations on 8 providers and return "ABCD".

`yacat.py` supports a few optional parameters. To get help on those, please type:

```python
python3 yacat.py --help
```

One of the interesting options is to have log output to a file. This can be achieved by adding the following option to the yacat.py run:

```python
--log-file LOG_FILE_NAME
```

## Other languages support

{% hint style="info" %}
The yacat example is written in Python using Golem's Python High-Level API \([YAPAPI](https://github.com/golemfactory/yapapi)\). Golem currently supports writing requestor agents using JavaScript/TypeScript High-Level API \([YAJAPI](https://github.com/golemfactory/yajsapi)\) also.
{% endhint %}

## Next steps

The complete reference of the Python High-Level API \(yapapi\) is available here:

{% page-ref page="../../yapapi/yapapi.md" %}

You can also have a look at our JavaScript/TypeScript API if you're interested in developing your requestor agent in JS/TS:

[https://github.com/golemfactory/yajsapi](https://github.com/golemfactory/yajsapi)

## Closing words

{% hint style="success" %}
Golem is waiting to serve your applications. Our decentralized - and open to everyone - platform is here \(now in alpha\).

We did our best to make developing Golem applications super easy.

Now it's time for your move!
{% endhint %}

And remember:

{% hint style="info" %}
In case of any doubts or problems, you can always contact us on discord.

[https://discord.com/channels/684703559954333727/756161015493951600](https://chat.golem.network)
{% endhint %}

