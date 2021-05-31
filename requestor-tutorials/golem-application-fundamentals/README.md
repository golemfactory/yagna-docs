# Golem application fundamentals

## What is a Golem application?

Now that you have seen a couple of simple Golem applications in action, it is a good idea to start from the beginning.

A Golem application consists of a certain number of execution units - e.g. VMs capable of running Docker images - launched within the network's provider nodes that are orchestrated by a requestor agent - a piece of code talking directly to the REST API on a requestor node.

Golem's execution units are theoretically capable of running code inside any environment that provides effective isolation of execution from the host. Currently Docker VMs and WASM are supported. 

So far, said orchestration takes the form of one of three types of actions:

* sending input files to the execution unit
* running commands on the execution unit
* getting output files back from the execution unit

![](../../.gitbook/assets/tutorial-05.jpg)

## How does a Golem application work?

### Components

A Golem application in general consists of two distinct components:

* **Requestor** agent - splits the computation problem into several parts, and sends them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
* **Provider** exe unit responsible for providing the computing resources. For applications based on VM runtime - the exeunit hosts a VM image, which executes the given part and returns results to the requestor.

In the case of a VM application, the Provider side is implemented as a docker image crafted for the desired purpose. It is the responsibility of the application's author to prepare a dedicated dockerfile that describes this custom image. Of course, it may happen that there already exists an image \(e.g. on Docker Hub\) that can be used directly - in such case, this step can be skipped.

### Execution flow

#### Requestor agent and market negotiation

The application's execution starts on the Requestor's end when the user runs the requestor agent.

After specifying and publishing a demand to Golem's market, the requestor agent receives offers from providers that meet its needs - e.g. having a sufficient amount of RAM.

#### Payload 

Once agreements with the selected providers are finalized, which happens in the course of an automated negotiation process, the providers are asked to deploy "payload" - the application component that will be executed \(eg. in case of VM runtime-based applications- load the appropriate image\).

{% hint style="info" %}
_If this is a subsequent run of the image, the image could already be cached by some of the providers._
{% endhint %}

#### Input data

The task is then split into fragments and each provider can receive one or more of such fragments. Each fragment is described by a certain set of input data - part of which can be common for the whole task and part of which may be specific for the given fragment. The prepared data is then sent - either directly from the memory, or from requestor's local file system - to the provider and further, into eg. the Docker container's file system on the provider's execution unit.

#### Execution script

A script consisting of one or more commands is executed by the execution unit using the providers' docker containers.

{% hint style="info" %}
It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor.
{% endhint %}

#### Output

The requestor agent needs to transfer the output files from the provider's docker container's file systems to its local file system.

The agent then combines all the data transferred from providers to form the final output that can be consumed by the application user.

#### Payments

As the provider executes the payload, it also expects the requestor to pay for the activity. The payments are driven by invoice & debit note artifacts issued by the provider, which must be acknowledged and accepted by the requestor agent. The Golem implementation orchestrates payments for the accepted invoices to be made using the payment platform/driver negotiated during the negotiation stage - so the requestor agent does not need to dive into the nuances of payments. 

To learn about some additional details on how different parts of Golem work together, please have a look at:

{% page-ref page="../../introduction/requestor.md" %}

{% page-ref page="../../introduction/provider.md" %}

{% page-ref page="../../introduction/golem-overview.md" %}

## High-level API libraries

The low-level mechanics of the Golem market are quite complex, and building robust applications using the low-level APIs, while possible, may not be the most efficient approach. For this reason, a concept of High-level API libraries has been designed, as "bindings" of specific programming languages with Golem platform.

The purpose of a high-level API is to wrap the intricacies of Golem APIs with more efficient programming models, based on computation models more intuitive, than Golem market, activity and payment concepts. A developer using these libraries should have a basic understanding of Golem platform's fundamental concepts \(Demand/Offer market matching, activity execution, payment-related logic\), but all the low-level logic is implemented in a high-level API library.

Following high-level API libraries are supported by Golem Factory:

{% page-ref page="../../yapapi/yapapi.md" %}

{% page-ref page="../../yajsapi/yajsapi.md" %}

## Task Model vs Service Model

Two basic computation models are supported by Golem high-level APIs.

* **Task model** is designed to support **batch processing**, where an application is expected to perform a set of "computation jobs" on Golem network. A high-level API library provides structure for a developer to define batch tasks, which are then efficiently orchestrated across a selected number of providers available in Golem network. Batch jobs may require input data to be shipped onto the provider side, and may produce output data, which needs to be fetched once the computation is complete.
* **Service model** is an abstraction over interactive processes which get launched, and operate in order to respond to requests. A service generally is expected to be active until explicitly stopped, however all the concepts of input/output data transfer also do apply.

Please refer to following sections for a dive into those two Golem programming models:

{% page-ref page="../task-processing-development/" %}

{% page-ref page="../service-development/" %}

