# Golem application fundamentals

## What is a Golem application?

Now that you have seen a simple Golem application in action, it is a good idea to start from the beginning.

A Golem application consists of a certain number of execution units - e.g. VMs capable of running modified Docker images - launched within the network's provider nodes that are orchestrated by a requestor agent - a piece of code talking directly to the REST API on a requestor node.

Golem's execution units are theoretically capable of running any kind of payload. Out of the box, we provide ability to execute code inside environments that provide effective isolation of execution from the host - currently, this support is limited to Docker-like VMs and WASM.

Other kinds of payloads are possible as long as the app developer is ready to [implement an appropriate runtime](https://github.com/golemfactory/ya-runtime-sdk/) and distribute it to willing providers.

So far, said orchestration takes the form of one of three types of actions:

* sending input files to the execution unit
* running commands on the execution unit and reading from their standard output or standard error streams
* getting output files back from the execution unit

![](../../.gitbook/assets/tutorial-05.jpg)

## How does a Golem application work?

### Components

A Golem application in general consists of two distinct components:

* **Requestor** agent - controls the work expected from the payload executed on provider side, eg. splits the computation problem into several parts, and sends them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
* **Provider** exe unit responsible for providing the computing resources. For applications based on VM runtime - the exeunit hosts a VM image, which executes the given part and returns results to the requestor.

In the case of a VM application, the provider side is implemented as a docker image crafted for the desired purpose. It is the responsibility of the application's author to prepare a dedicated dockerfile that describes this custom image. Of course, it may happen that there already exists an image \(e.g. on Docker Hub\) that can be used directly - in such case, this step can be skipped.

### Execution flow

#### Requestor agent and market negotiation

The application's execution starts on the requestor's end when the user runs the requestor agent.

After specifying and publishing a demand to Golem's market, the requestor agent receives offers from providers that meet its needs - e.g. having a sufficient amount of RAM.

#### Payload

Once agreements with the selected providers are finalized, which happens in the course of an automated negotiation process, the providers are asked to deploy "payload" - the application component that will be executed \(eg. in case of VM runtime-based applications - load the appropriate image\).

{% hint style="info" %}
_If this is a subsequent run of the image, the image could already be cached by some of the providers._
{% endhint %}

#### Execution script

A script consisting of one or more commands is executed by the execution unit using the providers' docker containers.

#### Input and output

As part of the execution script, the requestors may wish to supply the providers with additional data \(be it files or execution parameters\) that need to be transferred to the providers. Similarly, once some task has been executed on a provider node, the requestor agent may wish to transfer the output files from the provider to its local file system.

Appropriate upload/download commands are showcased in our more detailed tutorials in which we describe our two major development models: [the task model](../task-processing-development/) and [the service model](../service-development/).

#### Payments

As the provider executes the payload, it also expects the requestor to pay for the activity. The payments are triggered by invoices and debit notes issued by the provider, which must be acknowledged and accepted by the requestor agent. Golem's high-level API orchestrates payments for the accepted invoices to be made using the payment platform/driver negotiated during the negotiation stage - so the requestor agent does not need to dive into the nuances of payments.

To learn about some additional details on how different parts of Golem work together, please have a look at:

{% page-ref page="../../introduction/requestor.md" %}

{% page-ref page="../../introduction/provider.md" %}

{% page-ref page="../../introduction/golem-overview.md" %}

## High-level API libraries

The low-level mechanics of the Golem market are quite complex, and building robust applications directly using the low-level APIs, while possible, may not be the most efficient approach. For this reason, a concept of High-level API libraries has been designed, as "bindings" of specific programming languages with Golem platform.

The purpose of a high-level API is to wrap the intricacies of Golem APIs with more efficient programming models, based on computation models more intuitive than Golem market, activity and payment concepts. A developer using these libraries should have a basic understanding of Golem platform's fundamental concepts \(Demand/Offer market matching, activity execution, payment-related logic\), but all the low-level logic is implemented in a high-level API library.

Following high-level API libraries are supported by Golem Factory:

{% page-ref page="../../yapapi/yapapi.md" %}

{% page-ref page="../../yajsapi/yajsapi.md" %}

## Task Model vs Service Model

Two basic computation models are supported by Golem high-level APIs.

* **Task model** is designed to support **batch processing**, where an application is expected to perform a set of "computation jobs" on Golem network. A high-level API library provides structure for a developer to define batch tasks, which are then efficiently distributed across a selected number of providers available in Golem network. Batch jobs may require input data to be transferred to the provider side, and may produce output data, which needs to be fetched once the computation is complete.
* **Service model** is an abstraction over **interactive processes** which get launched, and operate in order to respond to requests. A service generally is expected to be active until explicitly stopped, however all the concepts of input/output data transfer also do apply.

Please refer to following sections for a dive into those two Golem programming models:

{% page-ref page="../task-processing-development/" %}

{% page-ref page="../service-development/" %}

