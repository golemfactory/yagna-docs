---
description: Your own thing on golem.
---

# Create your own application on golem

## Introduction

The use case for the Golem network is to be used by developers to create their own applications on Golem. The Golem platform and the Golem SDK are carefully crafted for this scenario.

This tutorial shows typical own application development with the Golem port of [Hashcat](https://hashcat.net/hashcat/) open source password cracking tool.

## Prerequisites

* Supported operating system
  * OS X 10.14+
  * Ubuntu 18.04 or 20.04
  * Windows 10
* Python 3.6+, git and yagna daemon installed, as described in 

{% page-ref page="../requestor-tutorials-1/flash-tutorial-of-requestor-development.md" %}

* Being familiar with Requestor and Provider concepts. Those are described here:

{% page-ref page="../introduction/requestor.md" %}

{% page-ref page="../introduction/provider.md" %}

* Your own idea that maps to the map-reduce model and can be implemented as running multiple docker images on golem providers. 

_Initially, you can start just by experimenting with our example yacat - Golem_ [_Hashcat_](https://hashcat.net/hashcat/) _port._

## How does it work?

Currently, Golem network supports the following application architecture:

* Application is divided into two parts:
  * **Requestor** \(sometimes called _a_ _master node_\). Divides the computation problem into several parts, and send them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
  * **Provider** \(sometimes called _worker node_\). Executes the given part and returns results to the requestor.
* The Provider side execution is implemented as the docker container.
* The application creator prepares a dedicated dockerfile that describes the image. 
  * _If there \(for example on the docker hub\) exist image that can be used directly, there is no need to create a custom image._
* The application starting point is the Requestor side, which runs the requestor agent.
* The requestor agent gets the providers that meet its needs from the market.
* The providers are asked to load the appropriate image. 
  * _If this is a subsequent run of the requestor, the image could already be cached by some of the providers._ 
* For each of the providers, the requestor prepared input data. Those are sent from the memory or local requestor's file system into the docker container's file system.
* One or several commands are executed on the provider's docker containers.
  * _It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor._
* Requestor transfers needed files from the provider's docker container's file systems.
* Requestor combines all the data from providers to form final output that can be consumed by the application user.

![](../.gitbook/assets/tnm-docs-infographics-06.jpg)

Some additional details can be found here:

{% page-ref page="../introduction/golems-details.md" %}



