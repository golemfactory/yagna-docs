---
description: Create your own task application on Golem
---

# Create your own task application using High-Level API

## Introduction

This tutorial is designed for developers who want to create their own application on the Golem network. 
It will guide you through the process of creating a task-based requestor application using the high-level API, and provide you with examples to help you understand the concepts better.

{% hint style="info" %}
If you have any questions or run into any issues while following this tutorial, please don't hesitate to reach out to us on our [Discord channel](https://chat.golem.network/) for help.
{% endhint %}

To make the tutorial easier to follow, it has been divided into several sections. In the first section, we will provide a general introduction to developing applications on the Golem network, and explain the task model that is used in Golem applications.

{% content-ref url="./task-model.md" %}
[Introduction to the task model](./task-model.md)
{% endcontent-ref %}

In the next section, we will walk you through the process of creating a simple example application that runs on the VM runtime. We will provide code examples and explain the mechanics of task-based requestor development.

{% content-ref url="./examples/hello.md" %}
[Task Example 0: Hello World!](./examples/hello.md)
{% endcontent-ref %}

{% content-ref url="./examples/simple.md" %}
[Task Example 1: Simple Usage of Task API](./examples/simple.md)
{% endcontent-ref %}

We will then show you how to use Golem to run a `hashcat` application in parallel. This section will provide an example of a more complex use case and explain how to use Golem's capabilities to run it efficiently.

{% content-ref url="./examples/hashcat.md" %}
[Task Example 2: Hashcat on Golem](./examples/hashcat.md)
{% endcontent-ref %}

Lastly, we will describe how to use the API directly from the browser context. This section will provide information on how to use the API in web applications and explain the benefits and limitations of this approach.

{% content-ref url="./examples/web.md" %}
[Task Example 3: Requestor in browser](./examples/web.md)
{% endcontent-ref %}