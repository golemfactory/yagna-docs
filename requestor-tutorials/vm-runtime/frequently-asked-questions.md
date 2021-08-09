# Frequently asked questions

### Why is it necessary to convert from a Docker image to .gvmi?

The most important reason for this is to reduce the size of the image being transferred. When converting to `.gvmi` all redundant layers from the Docker image are discarded and the filesystem itself gets compressed using [`squashfs`](https://www.kernel.org/doc/html/latest/filesystems/squashfs.html).

This results in a substantial size difference between the two images. For example, as of the time of writing this answer, the Docker image built as part of [Creating a Docker image](creating-a-docker-image.md) article is about `650 MB` in disk size. After conversion, the resulting `.gvmi` file weighs around `50 MB`. That's a 13x size difference!

But why do we need this? Most importantly, to reduce the setup time for providers downloading a new image, since this download time affects the computation time.

