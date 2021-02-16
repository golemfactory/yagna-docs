---
description: The provider actor in the Golem
---

# Provider

## What is a provider?

The role of a Provider agent is sharing hardware resources within the Golem network in return for GLM tokens.

A provider agent - as understood in the context of the Golem network - is a specific piece of code running on an Internet-connected device. The code implements the Golem network protocol, thus the machine running it acts as a Golem node.

In general, almost any computer might act as a provider. It can be a laptop, desktop, or a server machine. The particular resource details \(for example, the number of CPUs or its memory limit\) that are subject to sharing can be configured by the hardware owner.

{% hint style="info" %}
The provider binaries are available as a pre-built Linux installation package. You do not need to perform any development or extensive configuration to have a Golem provider up and running on your Linux machine.
{% endhint %}

{% page-ref page="../provider-tutorials/provider-tutorial.md" %}

## What does a provider do?

1. The Provider announces the availability of its resources in the Golem market. This is called an Offer.
2. The Golem market performs the matching between provider side \(Offers\) and requestor side  \(Demands\).
3. If there is a Requestor willing to use the Provider's resources, the Agreement is signed.
4. The resources are used by the Requestor \(for example by transferring input/output files and running a particular Golem VM Image, which is derived from docker image, on the Provider's hardware\).
5. The Provider bills the Requestor in GLMs.
6. The Requestor performs an [Ethereum](https://ethereum.org/) payment \(zkSync or ERC20\) for resource usage.

## How can I benefit from running a provider on my machine?

After installing and running the Golem Provider Agent you will start participating in the Golem Network in the following way:

* serving other actors in the Golem Network that are in need of computing resources, with your hardware that has idle capacity.
* receiving payments for the resources you share

The typical resource usage scenario is as follows: after receiving the input data, the processing is performed by your machine. Next, the output data is sent back to the requestor and the payment is executed through [Ethereum](https://ethereum.org/).

![](../.gitbook/assets/tnm-docs-infographics-02.jpg)

