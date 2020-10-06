---
description: Your own thing on golem.
---

# Create your own application on Golem

## Introduction

The use case for the Golem network is to be used by developers to create their own applications on Golem. The Golem platform and the Golem SDK are carefully crafted for this scenario.

This tutorial shows typical own application development with the Golem port of [Hashcat](https://hashcat.net/hashcat/) open source password cracking tool.

## Prerequisites

* Supported operating system
  * OS X 10.14+
  * Ubuntu 18.04 or 20.04
  * Windows 10
* Python 3.6+, git and yagna daemon installed, as described in 

{% page-ref page="../requestor-tutorials-1/flash-tutorial-of-requestor-development.md" %}

* Being familiar with Requestor and Provider concepts. To proceed, please first check those pages:

{% page-ref page="../introduction/requestor.md" %}

{% page-ref page="../introduction/provider.md" %}

* Your own idea that maps to the map-reduce model and can be implemented as running multiple docker images on golem providers. 

_Initially, you can start just by experimenting with our example yacat - Golem_ [_Hashcat_](https://hashcat.net/hashcat/) _port._

## How does it work?

Currently, Golem network supports the following application architecture:

* Application is divided into two parts:
  * **Requestor** \(sometimes called _a_ _master node_\). Divides the computation problem into several parts, and send them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
  * **Provider** \(sometimes called _worker node_\). Executes the given part and returns results to the requestor.
* The Provider side execution is implemented as the docker container.
* The application creator prepares a dedicated dockerfile that describes the image. 
  * _If there \(for example on the docker hub\) exist image that can be used directly, there is no need to create a custom image._
* The application starting point is the Requestor side, which runs the requestor agent.
* The requestor agent gets the providers that meet its needs from the market.
* The providers are asked to load the appropriate image. 
  * _If this is a subsequent run of the requestor, the image could already be cached by some of the providers._ 
* For each of the providers, the requestor prepared input data. Those are sent from the memory or local requestor's file system into the docker container's file system.
* One or several commands are executed on the provider's docker containers.
  * _It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor._
* Requestor transfers needed files from the provider's docker container's file systems.
* Requestor combines all the data from providers to form final output that can be consumed by the application user.

![](../.gitbook/assets/tnm-docs-infographics-06.jpg)

Some additional details can be found here:

{% page-ref page="../introduction/golems-details.md" %}

## Let's get to work. Dockerfile

{% hint style="info" %}
This example is made of two files:

* `yacat.Dockerfile` - the docker file used for provider's container images definition
* `yacat.py` - the golem port of hashcat

Those files can be found in `/examples/yacat` directory of [https://github.com/golemfactory/yapapi](https://github.com/golemfactory/yapapi)
{% endhint %}

Let's start with Dockerfile. We would need a dedicated one, to have [Hashcat](https://hashcat.net/hashcat/) ready to be used.

```text
FROM golemfactory/base:1.5

MAINTAINER Radek Tereszczuk <radoslaw.tereszczuk@golem.network>

RUN apt update

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

This is pretty standard Dockerfile. The main takeaways are:

* The `/golem/work` is our working directory. This is done by

```text
WORKDIR /golem/work
```

* We also need to define a dedicated volume for the `/golem/work` and other helping directories for possible future use.

```text
VOLUME /golem/work /golem/output /golem/resource
```

This makes `/golem/work` a place we will use for in / out file transfer.

We proceed with the `yacat.Dockerfile` with a standard docker build:

```python
docker build . -f yacat.Dockerfile -name rad9k/yacat
```

As Golem Network can not use raw docker images and need to use `gvmkit` image format, we need to convert the docker image to Golem \(`gvmkit`\) image. This will be done by:

```python
pip install gvmkit-build
gvmkit-build rad9k/yacat
gvmkit-build rad9k/yacat --push
```

The important fact is that in the end, int the console out, we are getting the `gvmkit` image hash, that looks like this:

```python
15912976e9d8ef5c82f6c918a0491c43cf4fb7b84b443013b36dd3fb
```

The details of docker image conversion are described here:

{% page-ref page="../requestor-tutorials-1/convert-a-docker-image-into-a-golem-image.md" %}

## What we want to achieve in this example

The [_Hashcat_](https://hashcat.net/hashcat/) __is a very powerful tool. To make our example simple, we will use it in a very basic manner.

The problem with [_Hashcat_](https://hashcat.net/hashcat/) __is the fact it often needs a lot of processing time \(days, months\) to find passowords, so this is a reason why we are going to make Golem Network version of Hashcat that will use computing power of many providers at the same time. Becouse passoword finding when done in parallel is much quickier, the parallel version will possibly run in hours and not days / months. 

But first we need to precisely define "finding password" problem. Let's assume we have hash made by processing an unknown password by phpass algorithm.

{% hint style="info" %}
Phpass is used as a hashing method by WordPress and Drupal. It is a public domain software and used with PHP applications.
{% endhint %}

The password hash is stored in in.hash file

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/
```

We assume we know that the password mask is:

```text
?a?a?a
```

That means that the password is made of 3 alpha characters.

Now we can try to find the password matching the given hash and mask, by calling:

```text
./hashcat -a 3 -m 400 in.hash ?a?a?a
```

The parameters used mean:

* `a 3` - use brute force type of attack
* `m 400` - password is hashed witch usage of phpass algorithm
* `in.hash` - name of a file containing the hashed password
* `?a?a?a` - mask to use

{% hint style="info" %}
The complete hashcat parameters reference is aviaible here: [https://hashcat.net/wiki/doku.php?id=hashcat](https://hashcat.net/wiki/doku.php?id=hashcat) 
{% endhint %}

As a result of the above call, the `hashcat.potfile` will be created with the following content:

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/:pas
```

where `pas` is the password that was unknown to us and has been cracked by the cat. 

Now let's try to make process of finding passwords to work in parallel.

## Doings things in parallel

How to make hash cat work in parallel? The answer is very simple: the keyspace concept. We can ask the cat to tell us what is the size of the possibility space for given mask and algorithm:

```text
hashcat --keyspace -a 3 ?a?a?a -m 400
```

as a result, we will have an answer in the `stdout`. In our case it is `9025`.

Now we can divide the `0..9025` space into separate parts. Assuming we want to use 3 providers, those parts would be:

* `0..3008`
* `3009..6016`
* `6017..9025`

To process the exact part of the whole `0..9025` space, we use following hashcat options:

```text
./hashcat -a 3 -m 400 in.hash --skip 3009 --limit 6016  ?a?a?a
```

The above call will process the `3009..6016t` part. If there is any result in that range it will be written to the `hashcat.potfile`.

Now we just need to:

* provide each docker container with `in.hash` file \(the same for all providers\)
* execute a command that uses proper skip / limit values in each docker container
* transfer `hashcat.potfile` from each docker container to the requestor
* check if any of the potfiles contains password. If yes, present it to the user.

## The requestor agent code

{% hint style="info" %}
Below we present an example of requestor agent code that makes Hashcat work in parallel.

You do not need to copy and paste the code below as it is available in `/examples/yacat/yacat.py` of the [https://github.com/golemfactory/yapapi](https://github.com/golemfactory/yapapi) repository.  
{% endhint %}

The requestor agent is written in Python and uses Golem's Python High Level API \(YAPAPI\). The details of the YAPAPI are described here:

{% page-ref page="../yapapi/yapapi.md" %}

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

```python
python3 yacat.py '?a?a?a' '$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/' --subnet-tag devnet-alpha.2
```

## Closing words

This is just a simple scenario example. The possibilities for our own Golem application are endless. We will provide more inspiring tutorials soon. 

{% hint style="info" %}
In case of any doubts or problems, you can always contact us on discord.

[https://discord.com/channels/684703559954333727/756161015493951600](https://discord.com/channels/684703559954333727/756161015493951600)
{% endhint %}





