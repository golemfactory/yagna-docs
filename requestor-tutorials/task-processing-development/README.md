---
description: Your own task on golem.
---

# Task Model development

{% hint style="warning" %}
The documentation is undergoing work. For the NodeJS or dApp articles, refer to the [new creator documentation](https://docs.golem.network/creators/).
{% endhint %}

## Introduction

This section shows a typical experience of a developer who would like to create their own task-based application using Golem.

{% hint style="info" %}
In case of any doubts or problems, you can always contact us on Discord.

[https://chat.golem.network](https://chat.golem.network/)
{% endhint %}

In order to make the journey through this tutorial easier to follow we divided it into sections.

The first one is a general introduction, pointing the developer's mind to the rails of Golem application development.

{% page-ref page="task-model-introduction.md" %}

Next we explain the mechanics of task-based requestor development, with a simple example running on the VM runtime:

{% page-ref page="task-example-0-hello.md" %}

Then we proceed to complicate things a bit by showing you how to use Golem with a proof-of-concept hash cracker:

{% page-ref page="task-example-1-cracker.md" %}

Last but not least, we describe `hashcat` and show how we are going to make it work in parallel using Golem.

{% page-ref page="task-example-2-hashcat.md" %}

