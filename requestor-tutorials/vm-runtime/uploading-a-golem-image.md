# Uploading a Golem image

## Pushing the image to a repository

Once your image is built and tested we can push it to a remote repository so that it becomes available to providers within the Golem network.

{% hint style="info" %}
For the sake of simplicity, we're currently using a freely-accessible repository that everybody can push into without any special requirements. This repository is managed by Golem Factory.

This is likely to change in the future, making it decentralized and adding an appropriate block-listing mechanism.

**Note that all code samples, libraries and tools use the Golem-managed image repo as default, it is not mandatory to use it - developers may publish their Golem images under any publicly accessible URL.**&#x20;
{% endhint %}

To push the image we use the same command that was used for conversion, adding the `--push` flag to it:

```
gvmkit-build golemfactory/blender:demo --push
```

{% hint style="warning" %}
You need to call the above command from a directory which contains your converted `.gvmi` image file.

In other words, it's currently not possible to convert and push an image with a single command - these need to be two separate steps.
{% endhint %}

Once the image is pushed, the tool will output its hash, e.g.:

`success. hash link 1a72390cbb08117b2d77373185e43701a747a3f7eb9a552c19aa5041`

**Make sure to save that hash** as you'll need it in the payload definition of your requestor agent.

That's it - your image is now published on Golem Factory's image repository.

{% hint style="warning" %}
Important: if you use a newly-pushed image in your task, you'll need to give providers some additional time to pull those images before they'll be able to publish offers that are compatible with your demand.
{% endhint %}

In other words, if you're running a task using a newly-pushed image, always specify a much longer task timeout on the first run.
