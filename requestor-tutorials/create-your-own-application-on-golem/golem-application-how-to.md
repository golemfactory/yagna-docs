---
description: High level view on Golem application.
---

# Golem application - how to

## What is the Golem application?

Golem application is just some docker containers \(Providers\) that are orchestrated by Python or JavaScript/TypeScript code \(Requestor\). The orchestration is realized as three types of actions: 

* sending input files to the docker container
* running commands on the container
* getting output files from the container 

![](../../.gitbook/assets/image%20%281%29.png)

## How does Golem application work?

Currently, Golem network supports the following application architecture:

* Application is divided into two parts:
  * **Requestor** \(sometimes called _a_ _master node_\). Divides the computation problem into several parts, and send them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
  * **Provider** \(sometimes called _worker node_\). Executes the given part and returns results to the requestor.
* The Provider side execution is implemented as the docker container.
* The application creator prepares a dedicated dockerfile that describes the image. 
  * _If there \(for example on the docker hub\) exist image that can be used directly, there is no need to create a custom image._
* The application starting point is the Requestor side, which runs the requestor agent.
* The requestor agent gets the providers that meet its needs \(for example having enough RAM\) from the Golem's market. 
* The providers are asked to load the appropriate image. 
  * _If this is a subsequent run of the image, the image could already be cached by some of the providers._ 
* For each of the providers, the requestor prepared input data. Those are sent from the memory or local requestor's file system into the docker container's file system.
* One or several commands are executed on the provider's docker containers.
  * _It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor._
* Requestor transfers needed files from the provider's docker container's file systems to local file system.
* Requestor combines all the data transferred from providers to form final output that can be consumed by the application user.

Some additional details can be found here:

{% page-ref page="../../introduction/provider.md" %}

{% page-ref page="../../introduction/requestor.md" %}

{% page-ref page="../../introduction/golems-details.md" %}

## How do I start?

First, you need to think about your computation problem in terms of parallel execution. Let's visualize your computation problem:

![](../../.gitbook/assets/image%20%288%29.png)

Now you need to find a way how to divide the whole problem into parts. Each part will be processed by different provider:

![](../../.gitbook/assets/image%20%287%29.png)

Now you need to have an idea how to:

1. Translate the problem fragments into in/out files and processing done on each of the providers.
2. Combine all the out files into the final problem solution.

## What do you need to create Golem application?

On the implementation level Golem application is made of two components:

1. Docker image that will run as a container on providers.
2. Requestor agent - a part of Pyhon / JavaScript / TypeScript code that will execute the problem dividing logic, orchestrate the providers and combine the output files to get the final result.

{% hint style="success" %}
Now you know what the Golem application is and how it works. 
{% endhint %}

Let's see how the implementation goes than! But first, let's understand how the hashcat that we are going to use as a reference can be made work in parallel.

