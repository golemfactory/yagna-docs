---
description: The provider actor in the golem network
---

# Provider

## What is a provider?

Technically speaking provider is some code running on Internet-connected hardware. The code implements the golem network protocol, thus the code acts as an actor in the golem network. 

The characteristic that describes the provider agent is the fact of sharing its hardware resources to the golem network. In practice, almost any computer might act as provider hardware. It can be a laptop, desktop or server machine. The particular resource details \(for example number of CPUs or memory limit\) that are subject to sharing can be configured by the hardware owner.

## What does a provider do?

* The provider announces the availability of its resources in the decentralized market. This announcement is called an offer.
* The decentralized market does the matching between provider side offers and requestor side demands.
* If there is a requestor willing to use provider resources, the transaction is arranged.
* The resources are used by the requestor \(for example by transferring input/output files and running a particular docker container on the provider's hardware\).
* The provider bills the requestor.
* The requestor performs [ethereum](https://ethereum.org/) payment for the resources usage

## How can I benefit from running the provider on mine hardware?

After installing and running the golem network provider you will benefit in the following way:

* serving other actors in the golem network that are in need of IT resources with your hardware that is currently not in use
* receiving payments for the resources your share

The payments are done through [ethereum](https://ethereum.org/), so the whole process is very simple!

The typical use case is as follows: after receiving input data, the processing is done by your hardware, output data being sent back to the requestor, the [ethereum](https://ethereum.org/) payment is done. It is that simple.

![Typical golem network use case](../.gitbook/assets/provider-tutorial-benefit.png)

## How I can become a golem network provider?

Becoming golem network provider is open to anyone. The installation and configuration are super easy. The details are described in the:

{% page-ref page="../tutorials/provider-tutorial.md" %}



