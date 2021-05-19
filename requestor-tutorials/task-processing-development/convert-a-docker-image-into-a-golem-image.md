---
description: >-
  This tutorial will show you how to prepare your own Golem image based on just
  any Docker image. This will allow you to port any apps that are able to work
  within Docker containers to New Golem.
---

# How to convert a Docker image into a Golem image?

## Prerequisites

### Docker

Since you're interested in running your own dockerized apps on Golem, we're going to assume you're more or less familiar with Docker.

Obviously, you'll need Docker itself installed on your machine. If you don't have docker, visit: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop) and download+install it.

### Python &gt;= 3.6.1

Our `gvmkit-build` tool requires a decently new Python version to run so please ensure you're running at least 3.6.1.

### gvmkit-build

This is our custom tool that prepares GVM images based on docker images.

To install it:

```text
pip install gvmkit-build
```

This will install `gvmkit-build` itself and all its dependencies.

## Building the image

There's just one command that suffices to build your Golem image. We're use our own example here but you can use any Docker image here:

```text
gvmkit-build golemfactory/blender:demo
```

This will pull the image if needed and then proceed with re-packing it into Golem's custom image format.

## Pushing the image to the repository

Once the image is built, it can be placed in our the repository.

{% hint style="info" %}
Currently, for the sake of simplicity, we're using a freely-accessible repository that everybody can push into without any special requirements to make the image available to all providers. This is likely to change in the future when we add an appropriate whitelisting mechanism.
{% endhint %}

To push the image:

```text
gvmkit-build golemfactory/blender:demo --push
```

Once the image is pushed, the tool will output its hash, e.g.:

`success. hash link 1a72390cbb08117b2d77373185e43701a747a3f7eb9a552c19aa5041`

Please **note down that hash** as you'll need it in the definition of the payload you'll want to run on Golem.

{% hint style="warning" %}
Important: if you use a newly-pushed image in your task, you'll need to give providers some additional time to pull those images before they'll be able to publish offers that are compatible with your demand.
{% endhint %}

In other words, if you're running a task using a newly-pushed image, always specify a much longer task timeout on the first run.

