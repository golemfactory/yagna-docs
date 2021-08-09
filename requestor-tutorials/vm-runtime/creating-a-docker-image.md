# Creating a Docker image

The first step to getting your code to run on a provider node is preparing a Docker image. This image will define the virtual machine in which your logic is going to be executed by provider nodes.

The below diagram depicts a simplified flow of interaction between the requestor agent and images running in runtimes on providers:

![](../../.gitbook/assets/image%20%2812%29.png)

{% hint style="info" %}
Note that in the diagram the name "Docker container" is used for simplicity.

In reality, providers are not running Docker images directly. Instead, the `.gvmi` format is used \(which is based on Docker images\). More information on this can be found in [Converting image from Docker to Golem](convert-a-docker-image-into-a-golem-image.md).
{% endhint %}

### Creating a Dockerfile

{% hint style="warning" %}
This tutorial assumes you are familiar with the basics of Docker \(including how to write a simple `Dockerfile`\).

If you need an introduction to Docker take a look at the official [Getting Started guide](https://docs.docker.com/get-started/) or one of the many third-party resources covering this topic.
{% endhint %}

Let's start with the definition for our image. We're going to use the following `Dockerfile`:

```text
FROM debian:latest
VOLUME /golem/input /golem/output
WORKDIR /golem/work
```

#### FROM

The `FROM` command specifies what existing image we want to use as our base. In this case we're using Debian Linux in its version tagged as `latest`. You can search for existing images using the [Docker Hub](https://www.hub.docker.com).

#### VOLUME

The next line uses a single `VOLUME` command to define two volumes: `/golem/input` and `/golem/output`.

When a Golem virtual machine is started, for each volume defined there will be a new directory created in the host's file system. This directory will then be made available inside the VM under it's specified path \(for example `/golem/input`\).

{% hint style="danger" %}
An image intended to be used with Golem **must** specify **at least one** **volume** through the `VOLUME` command.
{% endhint %}

#### WORKDIR

Finally, we specify a working directory. This will be the default directory to be used in shell commands once the VM is running.

{% hint style="danger" %}
An image intended to be used with Golem **must** specify a **working directory** through the `WORKDIR` command.
{% endhint %}

### Building the image

Having the above `Dockerfile` we can now build an image based on that file. To do so, we're going to use Docker's `build` command:

```text
docker build -t golem-example .
```

The above command assigns the tag `golem-example` to its output image. Once it's finished we should see the message `Successfully tagged golem-example:latest` in the terminal's output.

To verify the image is created we can list all images available locally by running:

```text
docker images
```

We've just built our custom Docker image, nice! The next step is to convert this image to a format the Docker VM runtime can handle.

