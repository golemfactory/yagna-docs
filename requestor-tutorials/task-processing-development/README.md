---
description: Your own task on golem.
---

# Task Model development

## Introduction

This tutorial shows a typical experience of a developer who would like to create their own task-based application for Golem. To show you how things work here, we created yacat - Golem port of [Hashcat](https://hashcat.net/hashcat/) - open source password recovery tool.

{% hint style="info" %}
In case of any doubts or problems, you can always contact us on discord.

[https://chat.golem.network](https://chat.golem.network/)
{% endhint %}

In order to make the journey through this tutorial easier to follow, we divided it into sections. If you are eager to get your hands dirty right away, feel free to jump directly to examples. Otherwise, read on:

{% page-ref page="task-example-0-hello.md" %}

This is a detailed article explaining the mechanics of task-based requestor development, using a Blender example on VM runtime.

{% page-ref page="task-model-introduction.md" %}

This is a general introduction, pointing the developer's mind to the rails of Golem application development.

Here we describe `hashcat` and show how we are going to make it work in parallel.

{% page-ref page="task-example-2-hashcat.md" %}

This is the main course of this tutorial. The implementation steps needed to create your own Golem application!

{% page-ref page="task-example-1-cracker.md" %}

This is another example of a VM runtime-based Golem task application.

