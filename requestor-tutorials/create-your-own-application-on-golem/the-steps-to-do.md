---
description: List of actions needed to execute the yacat example.
---

# Tutorial steps

This section contains steps you need to execute in order to run our yacat example. As this tutorial is designed to inspire you and create your own Golem application, we will explain all the needed details of Golem application implementation.

## Before we begin

In order to develop applications for the Golem network, you need to install yagna daemon on your machine. Below there are Unix commands you need to run. More details \(possibly useful if you have a Windows machine\) can be found here:

{% page-ref page="../flash-tutorial-of-requestor-development.md" %}

So let's start...

```bash
curl -sSf https://join.golem.network/as-requestor | bash -
```

This will install the newest version of yagna in the requestor flavor. You might be asked to modify your `PATH` afterwards. In order to clean the files from previous yagna installs:

```python
rm -rf $HOME/.local/share/yagna
```

And now, let the yagna start:

```python
yagna service run
```

{% hint style="danger" %}
The terminal window where you hit `yagna service run`, that runs yagna daemon should stay in the background for all the development time. The yagna daemon is needed for your requestor agent to run.
{% endhint %}

Now in another terminal window type

```python
yagna app-key create requestor
yagna app-key list
```

Please copy the value of the `key` column and paste it into the `YAGNA_APPKEY` env variable setting command:

```python
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

Now a few commands more...

```python
yagna payment init -r
python3 -m venv ~/.envs/yagna-python-tutorial
source ~/.envs/yagna-python-tutorial/bin/activate
pip3 install -U pip
pip3 install certifi 
pip3 install -i https://test.pypi.org/simple/ --extra-index-url=https://pypi.org/simple/ yapapi==0.3.0a2
git clone https://github.com/golemfactory/yapapi.git
cd yapapi 
git checkout b0.3
cd examples/yacat
```

{% hint style="success" %}
Now we are done: 

* The yagna deamon is running in the background. 
* The `YAGNA_APPKEY` is set with the value of the generated app key.
* The payment is initialized  \(please mind that it needs initialization after each `yagna service run`\)
* The virtual python environment for our tutorial is activated
* Dependencies are installed and the `yapapi` repository \(containing the tutorial examples\) is cloned.
*  In your current directory there are two files that will be used and discussed in this example:
  * `yacat.Dockerfile` - the docker file used for provider's container images definition
  * `yacat.py` - entry point. Orchestration of the containers.
{% endhint %}

## Let's get to work. Dockerfile

Let's start with Dockerfile \(`yacat.Dockerfile`\). But do we always need a dedicated dockerfile for our own Golem application?

{% hint style="info" %}
Golem is designed to use existing docker images, so you can use any existing docker image. There are no Golem specific conditions to be met by the image.
{% endhint %}

If there \(for example on the [docker hub](https://hub.docker.com/)\) is no docker image you need, you will need to create a custom one. 

For the yacat example we are using following dockerfile \(`yacat.Dockerfile`\):

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

As Golem does not need any specific elements in the dockerfile, the `yacat.Dockerfil`is just a standard dockerfile. For the requestor agent code, we are going to discuss in the next chapeter, we need to know the volume name. This is the last line of the above dockerfile:

```text
VOLUME /golem/work /golem/output /golem/resource
```

This makes `/golem/work` a place we will use for in / out file transfer. We are defining other volumes for possible future usage also.

Now we proceed with the `yacat.Dockerfile` with a standard docker build:

```python
docker build . -f yacat.Dockerfile -t yacat
```

As Golem Network can not use raw docker images and need to use `gvmkit` image format, we need to convert the docker image to Golem \(`gvmkit`\) image. This will be done by:

```python
pip install gvmkit-build
gvmkit-build yacat
gvmkit-build yacat --push
```

The important fact is that in the end, int the console out, we are getting the `gvmkit` image hash, that looks like this:

```python
2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9
```

{% hint style="info" %}
This hash will identify our image when our Golem application will run. Please copy and save it somewhere as in the requestor agent code, we will need to pass it to the `Engine` object in order to have providers with the proper image used for the container instances.
{% endhint %}

The details of docker image conversion are described here:

{% page-ref page="../convert-a-docker-image-into-a-golem-image.md" %}

## The requestor agent code

Now let's look at the yacat core - the requestor agent. Please check the `yacat.py` file below.

{% hint style="info" %}
The critical fragments of the `yacat.py` will be described in the following sections of the tutorial. You can do just a quick scan over the below wall of code.
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

## So what is happening here? yacat high-level picture

### worker\_check\_keyspace

The first step is to **check the keyspace size**. This is done in 3 steps, executed only once on one provider:

1. Preparing `keyspace.sh` script with contains given password mask. As the `hashcat --keyspace -a 3 {mask} -m 400` command outputs the keyspace size to `stdout`, we need to redirect the command output to the `keyspace.txt` file. That is the job of `keyspace.sh` script that is just: `hashcat --keyspace -a 3 {mask} -m 400 > /golem/work/keyspace.txt`
2. Execute the `keyspace.sh` script on the container.
3. Transfer the `keyspace.txt` file back to the requestor.

![](../../.gitbook/assets/image%20%283%29.png)

Knowing the keyspace size we can start looking for the password using many providers at the same time.

### worker\_find\_password

In order to look for passwords in the given keyspace range, for each of the providers we are executing the following 3 steps:

* Sending the `in.hash` file that contains password hash. 
* Executing `hashcat` with proper `--skip` and `--limit` values
* Getting the hashcat.potfile from the provider to the requestor

![](../../.gitbook/assets/image%20%284%29.png)

### read\_password

The final action is to scan over all the `*.potfiles` received. If there is a password, it will be displayed to the user.

## How does the code work?

### Package

To tell the Golem platform, what are our requirements for the providers we are going to get from the market, we are using the `package` object. The `image_hash` parameter tells that we want to use our image for the container. Here we use the hash received from the `gvmkit-build`. The `min_mem_gib` and `min_storage_gib` parameters specify memory and storage requirements for the provider.

```python
 package = await vm.repo(
     image_hash="2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9",
     min_mem_gib=0.5,
     min_storage_gib=2.0,
 )
```

### Engine

The `package` object is passed to the `engine` object with  several other options, such as:

*  `budget`defines maximal spendings for executing all the tasks on Golem
* `max_workers` defines maximal number of simultaneously running providers.
* `timeout` defines the timeout. This one is important to be big enough to include the image download time plus the computation time.
* `subnet_tag` specifies the providers net to be used. For example, you would not use mainnet network for tests.

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

### Main

Golem high-level API that we use to interact with the Golem network uses asynchronous programming a lot. The asynchronous execution starting point is at line 152:

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

In the `main` function, the most important fragments begins in the 100 line:

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

Having the `ranges` list we can call the `worker_find_password` for each of the providers passing only given `range`:

```python
async for task in engine.map(worker_find_password, [Task(data=range) for range in ranges]):
    print(
        f"{utils.TEXT_COLOR_CYAN}"
        f"Task computed: {task}, result: {task.output}"
        f"{utils.TEXT_COLOR_DEFAULT}"
    )
```

After all the providers return its hashcat.potifle we need to scan over each of them, as one of them possibly contains the password we are looking for:

```python
password = read_password(ranges)
```

### worker\_check\_keyspace

The `worker_check_keyspace` is also interesting. Here we need to  execute the following command on only one of the providers:

```python
hashcat --keyspace -a 3 {mask} -m 400
```

As this command is using `stdout` for the keyspace size information passing, we need the `stdout` to be captured. 

As we can not use `ctx.run` call directly to redirect stdout to `keyspace.txt`, we are preparing `keyspace.sh` file with the `hashcat --keyspace -a 3 {mask} -m 400 > keyspace.txt` content.

Now we need to send `keyspace.sh` to one of the providers running our image. And run

```python
ctx.run("/bin/sh","/golem/work/keyspace.sh")
```

Now we can transfer the `keyspace.txt` back to the requestor

```python
output_file = "keyspace.txt"
ctx.download_file(f"/golem/work/keyspace.txt", output_file) 
```

### worker\_find\_password

## Example run

\[i tylko jedna linijka????\]

```python
python3 yacat.py '?a?a?a' '$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/' --subnet-tag devnet-alpha.2
```

The above execution should return "pas" as a guessed password being computed on the default number of providers being 3.

A more computation-intensive example is:

```python
python3 yacat.py '?a?a?a?a' '$H$5ZDzPE45C.e3TjJ2Qi58Aaozha6cs30' --subnet-tag devnet-alpha.2 --number-of-providers 8
```

The above command should execute computations on 8 providers and return "ABCD".

## Next steps

The requestor agent is written in Python and uses Golem's Python High Level API \(YAPAPI\). The details of the YAPAPI are described here: \[dac nizej - next steps\]

## Closing words

This is just a simple scenario example. The possibilities for our own Golem application are endless. We will provide more inspiring tutorials soon. \[za malo emphasis ze mozesz robic swoje\]

{% hint style="info" %}
In case of any doubts or problems, you can always contact us on discord. \[dac na poczatku zeby sie nie bali\]

[https://discord.com/channels/684703559954333727/756161015493951600](https://discord.com/channels/684703559954333727/756161015493951600)
{% endhint %}







