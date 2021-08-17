---
description: >-
  This tutorial will show you how to prepare your own Golem image based on an
  arbitrary Docker image.
---

# Converting an image from Docker to Golem

## Prerequisites

### Docker

You are going to need Docker itself installed on your machine. If you don't have it set up yet follow these instructions: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

### Python &gt;= 3.6.1

Our `gvmkit-build` tool requires a decently new Python version to run so please ensure you're running at least 3.6.1. You can check your system's Python version by running:

```text
python --version
```

### gvmkit-build

This is our custom tool that prepares Golem VM images based on Docker ones.

You can install it using Python's `pip` command:

```text
pip install gvmkit-build
```

This will install `gvmkit-build` itself along with all its dependencies.

## Converting the image

For the sake of this exercise let's assume we're using an image named `golem-example` with the `latest` tag. Keep in mind that the same method will apply to just about any Docker image.

{% hint style="info" %}
If you want to use a custom Docker image you'll first have to build it. You can follow the [Creating a Docker image](creating-a-docker-image.md) tutorial to learn more.
{% endhint %}

To convert the chosen image to the Golem VM format we're going to call the following command:

```text
gvmkit-build golem-example:latest
```

This makes use of the `gvmkit-build` package installed as part of this tutorial's prerequisites.

If everything went well then you should see a file called `golem-example-latest-{...}.gvmi` in the directory from which you invoked the `gvmkit-build` command. The actual name of the file includes a fragment of the image's hash \(in place of `{...}` in this example\).

{% hint style="info" %}
It's possible to use `gvmkit-build` with images from remote Docker repositories \(Docker Hub, for example\).

You can use the `name:tag` format directly - if the requested image is not available locally it will be pulled first.
{% endhint %}

That's it, we now have an image file that can be executed using Golem's VM runtime!

Before using your image in the Golem network it's a good idea to first run it locally and make sure it works as intended.

{% hint style="warning" %}
Testing using the base Docker image may not be enough! It's always best to test using the exact same artifact the providers are going to use. In this case, it's the `.gvmi` image.
{% endhint %}

You can learn how to run your image locally here:

{% page-ref page="gvmi-debugging.md" %}

When you're ready to publish your image - take a look here:

{% page-ref page="uploading-a-golem-image.md" %}

