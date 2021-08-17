# VM runtime

## Introduction

In this section we're going to take a closer look at Golem's primary execution environment - the **virtual machine runtime**.

This runtime allows provider nodes to run Docker-like images defined by Golem app developers.

Before we focus on specifics of the VM runtime let's first establish what we mean by "runtime" in Golem's context.

{% hint style="info" %}
A **runtime** \(also known as an execution unit, or exe-unit\) is a binary used by the Golem daemon \(yagna\) on provider nodes.

A given runtime is responsible for running a certain type of an image \(for example, we have separate runtimes for VMs and for WASM code\).
{% endhint %}

In the case of Golem VMs, the runtime being used is [`ya-runtime-vm`](https://github.com/golemfactory/ya-runtime-vm).

## Preparing a VM image

### 1. Creating a Docker image

The first step is building a Docker image our VM will be based on. Usually this is achieved by defining a `Dockerfile` which describes what kind of a machine we need along with some custom configuration.

To learn more about creating such an image take a look here:

{% page-ref page="creating-a-docker-image.md" %}

### 2. Converting to .gvmi format

Golem's VM runtime does not use Docker images directly. Instead, it uses `.gvmi` files - a format developed internally to greatly reduce image size compared to Docker.

Converting a Docker image to `.gvmi` is described here:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}

### 3. Testing and debugging

When developing a Golem application it's important to test the final `.gvmi` image rather than it's base Docker image. This is because there are some important differences between the two which may affect the application code.

To learn about running Golem VM images locally using `ya-runtime-dbg` take a look here:

{% page-ref page="gvmi-debugging.md" %}

### 4. Uploading and using the image

Once an image is ready to be used within the Golem network it needs to be uploaded to a well-known repository so that it can be downloaded by provider nodes.

The below section covers image uploading and how to refer to this image in requestor agent code:

{% page-ref page="uploading-a-golem-image.md" %}

### 5. Frequently asked questions

In case of issues or uncertainties around the Golem VM runtime or image development - make sure to take a look at this dedicated FAQ section:

{% page-ref page="frequently-asked-questions.md" %}

