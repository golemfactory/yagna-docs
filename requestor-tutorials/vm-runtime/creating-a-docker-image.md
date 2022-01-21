---
description: Preparing payload for Golem's VM runtime
---

# Creating a Docker image

The first step to getting your code to run within the VM runtime on a provider node is preparing a Docker image. This image will define the contents of the virtual machine which is going to be executed by provider nodes.

The below diagram depicts a simplified, example flow of interaction between the requestor agent and containers running on providers:

![](<../../.gitbook/assets/image (12).png>)

{% hint style="info" %}
Note that in the diagram the name "Docker container" is used for simplicity.

In reality, providers are not running Docker images directly. Instead, the `.gvmi` format is used (which is based on Docker images). More information on this can be found in [Converting image from Docker to Golem](convert-a-docker-image-into-a-golem-image.md).
{% endhint %}

## Creating a Dockerfile

{% hint style="warning" %}
We're assuming here that you are familiar with the basics of Docker (including how to write a simple `Dockerfile`).

If you need an introduction to Docker take a look at the official [Getting Started guide](https://docs.docker.com/get-started/) or one of the many third-party resources covering this topic.
{% endhint %}

Let's start with the definition for our image. We're going to use the following `Dockerfile`:

```
FROM debian:latest
VOLUME /golem/input /golem/output
WORKDIR /golem/work
```

### FROM

The `FROM` command specifies what existing image we want to use as our base. In this case we're using Debian Linux in its version tagged as `latest`. You can search for existing images using the [Docker Hub](https://www.hub.docker.com).

### VOLUME

![Structure of a VM container on a provider's node](../../.gitbook/assets/requestor-vm-comms.jpg)

#### Input/Output

If your application requires transferring files to and/or from the provider node, you'll need to specifically define a place (or places) in the container's file system that will be used for file transfers. These places are called **volumes**.

The above is necessary since while the code running inside the VM has regular access to the whole filesystem, Golem's VM supervisor can only transfer files to and from specifically defined volumes.

In our example here, two volumes are created - one for incoming file transfers (`/golem/input`) and one for outgoing ones (`/golem/output`):

```
VOLUME /golem/input /golem/output
```

When a Golem virtual machine is started, a new directory is created in the host's file system for each of the defined volumes. This directory is then made available inside the VM under its specified path (for example: `/golem/input`).

#### Task-based API vs filesystem contents

Golem's Python and JS API libraries both expose the task-based model of execution, or in other words, an interface to treat the requestor's problem as a series of tasks which independently get scheduled for execution on a certain number of workers.

At the same time, a single worker is bound to a single activity on a provider node. Thus, the activity - that is, the specific VM container in case of the VM runtime - remains running as long as the respective worker is running on the requestor's end.

Coming back to the VM's filesystem and volumes, that means that within the lifetime of the worker, the state of the filesystem is persistent. One consequence is that any filesystem changes - be it updates to volumes or to other locations within the VM - performed within a single execution of a task will still be present when subsequent tasks get executed within the same worker.

#### Large files

Another aspect worth mentioning is that any filesystem changes, made to locations within the VM that are not defined as volumes, are kept within the host's RAM. That means, that if your provider-side code generates large temporary files, they'd best be stored within directories defined using the VOLUME clause.

As volume contents are stored on host's disk drives, their capacity limit will usually be larger than the storage available in RAM.

### WORKDIR

Finally, we specify a working directory. This will be the default directory to be used in shell commands once the VM is running.

### Important note about Docker's ENTRYPOINT

Because of how Golem's VM execution unit works, the Docker's `ENTRYPOINT` statement  is effectively ignored and replaced with the exeunit's own entrypoint.

The net effect for you, the developer, is that you need to pass the relevant initialization commands as part of the execution script running after the image is deployed and started on provider's VM.

## Building the image

Having the above `Dockerfile` we can now build an image based on that file. To do so, we're going to use Docker's `build` command:

```
docker build -t golem-example .
```

The above command assigns the tag `golem-example` to its output image. Once it's finished we should see the message `Successfully tagged golem-example:latest` in the terminal's output.

To verify the image is created we can list all images available locally by running:

```
docker images
```

We've just built our custom Docker image, nice! The next step is to convert this image to a format the Docker VM runtime can handle.
