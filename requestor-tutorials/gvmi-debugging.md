---
description: How to test and debug a .gvmi image on your machine
---

# Debugging a Golem image

### Introduction

When creating your own Golem app, one of the steps is defining a Docker image for your application. You can find a more detailed description of this process in our `Hello World` requestor tutorial.

{% page-ref page="task-processing-development/create-your-own-application-on-golem/hello-world.md" %}

Such a Docker image, after being converted to Golem's `.gvmi` format, is going to be used by providers within the Golem network.

There's one problem here - once you have a `.gvmi` image, how do you efficiently test it before sending it out to providers? In this tutorial we're going to explore `ya-runtime-dbg`, a tool built specifically for debugging user-built images.

{% hint style="info" %}
This tutorial assumes that you're already familiar with Docker and the basics of building a Golem application.
{% endhint %}

### Installation

{% hint style="warning" %}
`ya-runtime-dbg` is currently available for Linux **only**.
{% endhint %}

You can download the latest `.deb` package from the project's [releases page](https://github.com/golemfactory/ya-runtime-dbg/releases) and install it using `dpkg`:

```text
sudo dpkg -i path/to/.../ya-runtime-dbg_v0.2.0_amd64.deb
```

`ya-runtime-dbg` requires one of the available Golem runtimes to be available on your system.

{% hint style="info" %}
A Golem runtime is the execution environment for an app image. For example, [`ya-runtime-vm`](https://github.com/golemfactory/ya-runtime-vm) uses a virtual machine to run an image.
{% endhint %}

To verify your installation, try running the below command:

A set of default runtimes can be installed by the `yagna` provider installer:

```text
curl -sSf https://join.golem.network/as-provider | bash -
```

After using the installer your runtime binaries should be present under `~/.local/lib/yagna/plugins`\(again, we're assuming Linux as it's the only supported platform for `ya-runtime-dbg` for now\).

Alternatively, you can download a runtime package manually from its releases page \(e.g. [VM runtime](https://github.com/golemfactory/ya-runtime-vm/releases)\).

Later on we're going to see how to specify the runtime to be used by the debugger.

### Running an image

For the purpose of this tutorial we're going to focus on VM runtime debugging.

#### 1. Building an image

Let's start with creating our image. We're going to use the following `Dockerfile`:

```text
FROM debian:latest
VOLUME /golem/input /golem/output
WORKDIR /golem/work
```

To keep things simple, we use `debian:latest` as our base image.

The next line defines two volumes that will be mounted under `/golem/input` and `/golem/output` inside the VM. These directories will be shared with the host machine to allow for providing input and obtaining output from the VM.

Finally, we specify a working directory, which will be the starting location inside the VM once it's running.

We can now build a Docker image based on this file:

```text
docker build -t runtime-dbg-example .
```

The above command assigns the tag `runtime-dbg-example` to its output image. Once it's finished we should see the message `Successfully tagged runtime-dbg-example:latest` in the terminal's output.

With our Docker image ready, the last step is to convert it to the `.gvmi` format, so that it can be used with Golem's VM runtime. To do so, we're going to use the `gvmkit-build` tool:

```text
gvmkit-build runtime-dbg-example:latest
```

To learn more about `gvmkit-build` \(and how to install it\), please refer to this page from the handbook:

{% page-ref page="task-processing-development/convert-a-docker-image-into-a-golem-image.md" %}

Once the above command is finished we should have a `.gvmi` file in the directory from which we invoked the command. This file is ready to be used together with Golem's VM runtime.

#### 2.  Running the debugger

Let's now see how we can use `ya-runtime-dbg` together with our image. We can learn about the program's required arguments by calling `ya-runtime-dbg --help`:

```text
USAGE:
    ya-runtime-dbg [FLAGS] [OPTIONS] --runtime <runtime> --task-package <task-package> --workdir <workdir> [varargs]...
```

The program has three mandatory arguments:

* `--runtime` path to the Golem runtime we want to use,
* `--task-package` path to the package \(i.e. image\) we'd like to debug,
* `--workdir` path to the directory that will store directories mounted as volumes inside the image.

{% hint style="danger" %}
Please note: the program does not support **relative paths** \(i.e. paths relative to your shell's present directory\).
{% endhint %}

Let's now run the debugger supplying it with appropriate parameters:

```text
ya-runtime-dbg \
    --runtime ~/.local/lib/yagna/plugins/ya-runtime-vm/ya-runtime-vm \
    --task-package ~/.../docker-runtime-dbg-example-latest-be31909af5.gvmi \
    --workdir /tmp/workdir
```

The command is split into multiple lines using `\` so that it's easier to read. Some remarks related to the above call:

1. The path in `--task-package` needs to be changed so that it points to where you built your `.gvmi` file from the previous step.
2. `/tmp/workdir` is an example path, it may not exist on your system. You can create it by calling `mkdir /tmp/workdir` or use some other location.

Running the command should produce output similar to this:

```text
[INFO] Deploying
{"valid":{"Ok":""},"vols":[{"name":"vol-20c86845-e4ef-46a2-9137-d777c66703df","path":"/golem/input"},{"name":"vol-f61c0ce8-dc63-41ca-9f1d-54e020a1ac6b","path":"/golem/output"}],"startMode":"blocking"}
[INFO] Starting
[INFO] Entering prompt, press C-d to exit
```

Followed by a prompt character \(`▶`\). This indicates the debugger is now ready to be used!

#### 3. Using the debugger

With the debugger running we now have full access to our virtual machine!

The debugger provides us with an interactive shell which, by default, uses `bash`\(indicated by the name next to the prompt character\). This means we can use regular command line tools, for example:

```text
bash ▶ pwd
/golem/work
```

Calling `pwd` \(present working directory\) returns `/golem/work`, matching the path we specified in `WORKDIR` in our original `Dockerfile`.

This interactive prompt gives us full access to the virtual machine. For example, we could run the program or script that is normally executed by a provider.

Now, let's see how we can interact with the mounted volumes. First off, let's take a closer look at the startup output from the debugger \(specifically, the `vols` field from the second line\):

```text
[
  {
    "name": "vol-32e25157-5865-4fd2-9d35-909cd9893682",
    "path": "/golem/input"
  },
  {
    "name": "vol-1e319bdb-8d07-4d7b-b480-c076ee779f5d",
    "path": "/golem/output"
  }
]
```

This tells us about the directory mapping between our host machine and the virtual machine. The host directories are created under the path we specified as `--workdir` when starting the debugger \(in our case it's `/tmp/workdir`\).

Let's say we'd like to provide some data to the VM. We can do so by creating a file in the host directory that's mapped to `/golem/input` inside the VM. Looking at the mapping definition above, this directory is going to be `/tmp/workdir/vol-32e25157-5865-4fd2-9d35-909cd9893682`:

```text
echo "stuff" > /tmp/workdir/vol-32e25157-5865-4fd2-9d35-909cd9893682/data.txt
```

With the debugger still running, let's now verify that this file is accessible inside our VM. Using the debugger prompt let's issue the below command:

```text
bash ▶ cat /golem/input/data.txt
stuff
```

Success! Our input data is there and can be read by the VM.

{% hint style="info" %}
`ya-runtime-dbg` is going to create new directories for volumes in each run.
{% endhint %}

Once you're done debugging or want to restart the VM, press `Ctrl+D` while in the debugger prompt.

### Summary

`ya-runtime-dbg` provides us with the **exact same** environment a provider would use to execute our image. This allows for more accurate testing compared to running the original Docker image manually.

Here are some other advantages of using this debugger while developing a Golem application:

* shorter iteration times while working on the payload for the provider,
* isolated testing: no need to run the entire application,
* fully controlled, local environment with access to mounted volumes,
* full shell access to the virtual machine.

