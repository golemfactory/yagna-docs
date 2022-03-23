# Uploading a Golem image

## Pushing the image to a repository

Once your image is built and tested we can push it to a remote repository so that it becomes available to providers within the Golem network.

{% hint style="info" %}
For the sake of simplicity, we're currently using a freely-accessible repository that everybody can push into without any special requirements. This repository is managed by Golem Factory.

This is likely to change in the future, making it decentralized and adding an appropriate block-listing mechanism.

**Note that all code samples, libraries and tools use the Golem-managed image repo as default, it is not mandatory to use it - developers may publish their Golem images under any publicly accessible URL.**
{% endhint %}

To push the image we use the same command that was used for conversion, adding the `--push` flag to it:

```
gvmkit-build golem-example:latest --push
```

{% hint style="warning" %}
You need to call the above command from a directory which contains your converted `.gvmi` image file.

In other words, it's currently not possible to convert and push an image with a single command - these need to be two separate steps.
{% endhint %}

Once the image is pushed, the tool will output its hash, e.g.:

`success. hash link 1a72390cbb08117b2d77373185e43701a747a3f7eb9a552c19aa5041`

**Make sure to save that hash** as you'll need it in the payload definition of your requestor agent.

That's it - your image is now published in Golem Factory's image repository.

{% hint style="warning" %}
Important: The larger the images you use, the more additional time you'll need to give providers to pull those images before they'll be able to start your activities.
{% endhint %}

In other words, you always need to include the time needed to pull an image in the task timeout (or service expiry time). That's especially important if you're using a newly-pushed image for the first time.
