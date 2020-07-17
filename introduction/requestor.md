---
description: The requestor actor in the Golem
---

# Requestor

## What is a requestor?

Technically speaking the Golem requestor is some code running on Internet-connected hardware.

The characteristic that describes the requestor agent is the need to use hardware resources that are available in the Golem being shared by providers. 

{% hint style="info" %}
Because local hardware resources on the mobile device or even server machine are always limited, there is always some task that local, requestor's hardware can not perform in a reasonable time frame or not at all \(for example becouse of memory limit\).

There is no limit on the resources available in Golem. Requestor can use as much resources he needs.  In parallel.
{% endhint %}



## What does a requestor do?

The typical use case for the requestor is as follows:

* **Define the need**

Define the IT resources it needs. Those needs \(for example CPU and memory requirements\) would be than by the golem infrastructure published in the decentralized network in a form of so-called Demand. 

* **Buy the resources**

If in the decentralized market there are Offers that match requirements of the Order, the resources offered by the provider are both to be used by the requestor.

* **Use the resources**

The actual usage depends on the resources. For now, the most common scenario is performing computations, but the golem network is not limited to this use case.

* **Pay for the resources usage**

The last step is to pay for the usage of the resources \(unless the provider is offering them for free :\). There are many possible payment scenarios, but [Ethereum](https://ethereum.org/) based payment is the default one.

## How can I benefit from being a requestor?

The typical benefit for the requestor is being able to have instant access to a very large pool of computational hardware.  Instead of using local hardware, the requestor is able to use IT resources available on the decentralized market. 

**Please bear in mind that one requestor can use hardware from many providers at the same time.** Think about training a large ML model in seconds instead of hours. This is just an example, as there are many interesting business use cases described in the:

{% page-ref page="../tutorials/developing-a-golem-network-based-product.md" %}

## Requestor details

For the basic computations scenario the details of the resource usage are as follows:

* Specify what docker image to use/create a custom docker image.
* For each of the used providers \(there is no limit here on the number :\) define the files containing the input data for the computations.
* For each of the docker containers being created on the provider's hardware:
  * Input files are transferred to the docker container file system.
  * Execution of the "run task" command.
  * Output files are transferred from the docker container file system to the requestor.

