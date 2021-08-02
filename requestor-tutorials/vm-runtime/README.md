# VM runtime

The VM runtime \(GitHub: [`ya-runtime-vm`](https://github.com/golemfactory/ya-runtime-vm)\) is an ExeUnit implementation of a Docker-like runtime environment for Linux systems.

The runtime package consists of two modules:

* `ya-runtime-vm`

  An application for running Virtual Machine images pre-built for yagna. 

* `gvmkit`

  A tool for converting Docker images into yagna Virtual Machine images and uploading them to a public repository. Requires for [Docker](https://docs.docker.com/engine/install/ubuntu/) to be installed on your system. 

See the following article for instructions on building images for the VM runtime:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}

Debugging Golem images defined for VM runtime is a useful technique, described in this tutorial:

{% page-ref page="gvmi-debugging.md" %}

