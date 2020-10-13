---
description: Solution architecture and details.
---

# Golem overview

## Solution architecture

![](../.gitbook/assets/image%20%2810%29.png)

Golem is defined by the Golem network protocol. The Golem network is made by nodes that implement the Golem network protocol. We provide a default implementation of the Golem network protocol in form of the so-called Golem daemon.

The nodes in the Golem network run Golem daemon acting as providers or requestors. Both requestor and provider share the same Golem daemon. 

The diagram above shows the solution architecture of the Golem network. For simplicity, it shows just one requestor and one provider.   

### Requestor

The requestor logic is implemented as a **requestor agent**. The requestor agent is code that runs on requestor machine and communicates via REST with golem daemon's local http server. 

Currently, Golem supports writing requestor agent code in Pyhon and JavaScript/TypeScript languages. Writing reqeustor agent code is super easy as requestor agent is using dedicated High-Level API:

* For Python we have prepared High-Level API called [YAPAPI](https://github.com/golemfactory/yapapi). 
* [YAJSAPI](https://github.com/golemfactory/yajsapi) is High-Level API for JavaScript/TypeScript version developers. Currently in alpha. 

_Please mind the "ALT"  frame in the diagram above: typically the requestor contains application code in only one language. There are two "ALT" frames to show two possible scenarios._

More information on requestor are here:

{% page-ref page="requestor.md" %}

### Provider

The provider logic is implemented as a **provider agent**.  Provider agent is code that runs on provider machine and communicated via REST with the golem daemon.

The provider can offer its resources with help with many types of so-called **exe units**. Currently Golem supports:

* VM exe unit that run docker images and exposes interaction with the container
* WASM exe unit that runs WASM code

_Please mind the "ALT"  frame in the diagram above: the provider uses only one exe unit in the same time. There are two "ALT" frames to show two possible scenarios._

More information on provider are here:

{% page-ref page="provider.md" %}

## Developing applications for Golem

We provide a complete implementation of all the common elements for requestor and provider nodes. For you as a Golem application developer, there are just two dedicated components to provide - those are marked as "application code" above. Those are:

* **Requestor agent application code**

Defines the resource demands and orchestrates the task execution.

* **Docker image application code**

Defines the actual code that performs the tasks on the provider's hardware.

