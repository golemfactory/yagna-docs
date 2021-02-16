---
description: Solution architecture and details.
---

# Golem overview

## Golem architecture

![](../.gitbook/assets/tutorial-06%20%281%29.jpg)

Golem is a network of nodes that implement the Golem network protocol. We provide the default implementation of such a node in the form of the Golem daemon, called [yagna](https://github.com/golemfactory/yagna).

The nodes in the network can act as providers or requestors. Both the requestor and the provider share the same implementation of the Golem daemon.

The diagram above shows the architecture of the network. For the sake of simplicity, it shows just one requestor and one provider.

### Requestor

The requestor logic is implemented as a **requestor agent**, which is a piece of code that runs on the requestor's machine and communicates via REST with the Golem daemon's http server, usually running on the same machine.

A requestor agent can be written in any language as long as it's able to talk to the daemon's REST API. To make things easy for the developers though, we provide two high-level API libraries[: yapapi](https://github.com/golemfactory/yapapi) for Python 3.6+ and [yajsapi](https://github.com/golemfactory/yajsapi), our JS/TS API runnable under nodejs.

_Please note the "ALT" frames in the left part of the diagram above: there are two APIs that we support but a typical requestor agent contains application code in only one language and hence, will use only one of those alternatives._

For more information regarding a Golem requestor, have a look at:

{% page-ref page="requestor.md" %}

### Provider

The provider logic is implemented as a **provider agent** which is a piece of code that runs on the provider's machine and communicates via REST with the Golem daemon.

The provider can make its resources available to the requestors with the help of many types of **execution units** \(exe-unit for short\). Currently, Golem supports:

* VM exe unit that runs Docker images and allows for an interaction with the running container,
* and WASM exe unit that runs WASM code

_Please note the "ALT" frames in the diagram above: the provider uses only one exe unit at the same time out of the two available._

You can learn more about Golem providers here:

{% page-ref page="provider.md" %}

### Payments

The payments between requestors and providers are made through the [Ethereum](https://ethereum.org/) network using zkSync, a Layer2 solution that greatly improves cost-effectiveness. However, a user can also opt to use standard ERC-20 token transfers.

More on that here:

{% page-ref page="../payments/layer-2-payments-on-zksync.md" %}

and here:

{% page-ref page="../payments/using-golem-on-mainnet.md" %}

