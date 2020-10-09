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

## Lt's get to work. Dockerfile

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

{% endhint %}

The following code is described in detail in the next section of this tutorial.

```python
#!/usr/bin/env python3
import asyncio
import pathlib
import sys

from yapapi.log import enable_default_logger, log_summary, log_event_repr  # noqa
from yapapi.runner import Engine, Task, vm
from yapapi.runner.ctx import WorkContext
from datetime import timedelta

# For importing `utils.py`:
script_dir = pathlib.Path(__file__).resolve().parent
parent_directory = script_dir.parent
sys.stderr.write(f"Adding {parent_directory} to sys.path.\n")
sys.path.append(str(parent_directory))
import utils  # noqa

def write_hash(hash):
    f = open(str(script_dir / "in.hash"), "w")
    f.write(hash)
    f.close()

def write_keyspace_call(mask):
    f = open(str(script_dir / "keyspace.sh"), "w")
    f.write(f"hashcat --keyspace -a 3 {mask} -m 400 > keyspace.txt")
    f.close()

def read_keyspace():
    f = open(str(script_dir / "keyspace.txt"),"r")
    return int(f.readline())

def read_password(ranges):
    for r in ranges:
        f = open(str(script_dir / f"hashcat_{r}.potfile"),"r")
        line = f.readline()
        split_liset = line.split(":")
        if len(split_list) >= 2:
            return split_list[2]
    return None

async def main(args):
    package = await vm.repo(
        image_hash = "15912976e9d8ef5c82f6c918a0491c43cf4fb7b84b443013b36dd3fb",
        min_mem_gib = 0.5,
        min_storage_gib = 2.0,
    )

    async def worker_first(ctx: WorkContext, tasks):
        async for task in tasks:
            keyspace_sh_filename = str(script_dir / "keyspace.sh")
            ctx.send_file(keyspace_sh_filename, "/golem/work/keyspace.sh")
            ctx.begin()
            ctx.run("/bin/sh","/golem/work/keyspace.sh")
            output_file = "keyspace.txt"
            ctx.download_file("/golem/work/keyspace.txt", output_file)
            yield ctx.commit()   
            task.accept_task(result=output_file)

    async def worker_second(ctx: WorkContext, tasks):
        in_hash_filename = str(script_dir / "in.hash")
        ctx.send_file(in_hash_filename, "/golem/work/in.hash")

        async for task in tasks:
            skip = task.data
            limit = skip + step
            ctx.begin()
            ctx.run(f"hashcat -a 3 -m 400 in.hash --skip {skip} --limit {limit} {args.mask}")
            output_file = f"hashcat_{skip}.potfile"
            ctx.download_file(f"/golem/work/hashcat.potfile", output_file)
            yield ctx.commit() 
            task.accept_task(result=output_file)

    # beginning of the main flow

    write_hash(args.hash)
    write_keyspace_call(args.mask)
            
    # By passing `event_emitter=log_summary()` we enable summary logging.
    # See the documentation of the `yapapi.log` module on how to set
    # the level of detail and format of the logged information.
    async with Engine(
        package = package,
        max_workers = args.number_of_providers,
        budget = 10.0,
        # timeout should be keyspace / number of providers dependent
        timeout = timedelta(minutes = 25),
        subnet_tag = args.subnet_tag,
        event_emitter = log_summary(),
    ) as engine:

        async for task in engine.map(worker_first, [Task(data = None)] ):
            print(f"\033[36;1mTask computed: keyspace size count\033[0m")

        keyspace = read_keyspace()
        step = int(keyspace / args.number_of_providers)

        ranges: range = range(0, keyspace, step)

        async for task in engine.map(worker_second, [Task(data = range) for range in ranges]):
            print(f"\033[36;1mTask computed: {task}, result: {task.output}\033[0m")

        password = read_password()

        if password == None:
            print("\033[31;1mNo password found\033[0m")
        else:
            print(f"\033[32;1mPassword found: {password}\033[0m")  

if __name__ == "__main__":
    import pathlib
    import sys

    parser = utils.build_parser("yacat")

    parser.add_argument("--numberOfProviders", dest = "number_of_providers", type = int, default = 3)
    parser.add_argument("mask")
    parser.add_argument("hash")

    args = parser.parse_args()

    enable_default_logger(level = args.log_level)

    loop = asyncio.get_event_loop()
    task = loop.create_task(main(args))

    try:
        asyncio.get_event_loop().run_until_complete(task)
    except (Exception, KeyboardInterrupt) as e:
        print(e)
        task.cancel()
        asyncio.get_event_loop().run_until_complete(task)
```

## How does it work?

* To tell the Golem platform, that we want to use our image for the container, we use the hash received from the `gvmkit-build`

```python
 package = await vm.repo(
        image_hash = "15912976e9d8ef5c82f6c918a0491c43cf4fb7b84b443013b36dd3fb",
        min_mem_gib = 0.5,
        min_storage_gib = 2.0,
    )
```

* In order to proceed with the password cracking, first we need to determine what is the keyspace size. We will do it by executing

```python
hashcat --keyspace -a 3 {mask} -m 400 > keyspace.txt
```

as we need the `stdout` to be captured we are redirecting the command output to the `keyspace.txt` file

* As we can not use `ctx.run` call directly to redirect stdout to `keyspace.txt`, we are preparing `keyspace.sh` file with the `hashcat --keyspace -a 3 {mask} -m 400 > keyspace.txt` content.
* Now we need to send `keyspace.sh` to one of the providers running our image. And run

```python
ctx.run("/bin/sh","/golem/work/keyspace.sh")
```

* Now we can transfer the `keyspace.txt` back to the requestor

```python
output_file = "keyspace.txt"
ctx.download_file(f"/golem/work/keyspace.txt", output_file)
```

* The above is done by `worker_first`
* Now with the knowledge what is keyspace number, we can define range:

```python
step = int(keyspace / args.number_of_providers)
ranges: range = range(0, keyspace, step)
```

* For each range in the keyspace we will run separate provider \(that is what `worked_second` does\):

```python
async def worker_second(ctx: WorkContext, tasks):
    in_hash_filename = str(script_dir / "in.hash")
    ctx.send_file(in_hash_filename, "/golem/work/in.hash")

    async for task in tasks:
        skip = task.data
        limit = skip + step

        ctx.begin()

        ctx.run(f"hashcat -a 3 -m 400 in.hash --skip {skip} --limit {limit} {args.mask}")
        output_file = f"hashcat_{skip}.potfile"
        ctx.download_file(f"/golem/work/hashcat.potfile", output_file)

        yield ctx.commit()
  
        task.accept_task(result=output_file)
```

* In the end, we need to iterate through all the \*.potfile and see if there is any password there:

```python
def read_password(ranges):
    for r in ranges:
        f = open(str(script_dir / f"hashcat_{r}.potfile"),"r")
        line = f.readline()
        split_liset = line.split(":")
        if len(split_list) >= 2:
            return split_list[2]
    return None
```

* Finally, if something has been found, present it to the user.

```python
if password == None:
    print("\033[31;1mNo password found\033[0m")
else:
    print(f"\033[32;1mPassword found: {password}\033[0m")  
```

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







