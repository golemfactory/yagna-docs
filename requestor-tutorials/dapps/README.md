---
description: Deploying long-running, decentralized services on Golem using no-code tools.
---

# Decentralized applications on Golem

{% hint style="info" %}
Looking for a quick start?

[See how easy it is to run an application on Golem](run-a-dapp.md)
{% endhint %}

## Introduction

Golem is a network which enables its participants to make computing resources available for use by those who would wish to use them. From the perspective of requestors, among other uses, it allows services to be requested, deployed and run on the network’s providers.

The dApps on Golem project is a solution to deploy multi-layer apps on the Golem Network, without a need to dive into the APIs. Instead, the structure of the application is stored in YAML files, so the process may feel familiar for those of you who have some experience with e.g. docker-compose.

By a **dApp** - or a decentralized application, in the context of Golem, we understand such a combination of services and additional resources within the network, that together constitutes a full application, e.g. a website or a public API, running entirely on the Golem network.

Such services or decentralized applications can be run by virtually anyone as long as they have some GLM tokens to pay the providers for their work.

{% hint style="danger" %}
Please be aware that the dApps on Golem project is still in early access and should be considered experimental. Please [reach out to us on our community Discord](https://chat.golem.network/) if you'd like to help us improve these tools.
{% endhint %}

## Available experiments

While working with dApps, we created a few applications on top of it, which served us both as a testing ground and as a way to validate our approach. On the other hand, they were also designed to give you first a good starting point and later a reference when developing your own, similar apps.

### ToDo List Application [\[GitHub\]](https://github.com/golemfactory/dapp-experiments/tree/main/01\_todo\_app)

![ToDo List App](https://user-images.githubusercontent.com/5244214/201047967-f42dea7d-3e19-488b-9900-375f19badd96.png)

This application showcases utilizing the Golem Network to host a 3-layer application (**React** + **Flask** + **RQLite**)

### Weather Stats Application [\[GitHub\]](https://github.com/golemfactory/dapp-experiments/tree/main/weather\_stats)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Weather Stats App</p></figcaption></figure>

This application presents usage of the Golem Network with access to external services (not hosted on Golem) taking advantage of the outbound network connections.

## Components

### Golem Services

Golem [Service model](../service-development/README.md) describes a way to run specific Golem payloads and defines operations that need to be applied on state transitions throughout their lifetime. 

The payloads are the definitions of activities that a requestor wishes to be executed on Golem along with a complete set of parameters needed to initialize those activities. Those parameters can specify, e.g. what runtime and which container image to use or what the CPU or memory specifications are required by the payload.

An example of such a service could be e.g. a [web server that is to be deployed using Golem’s VM runtime](../service-development/service-example-3-vpn-simple-http-proxy.md) with a VM image containing an HTTP daemon, using a specific initialization script, exposed to the outside world using a specific gateway.

### Golem Deploy model

Building upon the foundations of the Golem’s Service model, the Golem Deploy model provides a way to describe sets of services that constitute full, multi-layered applications using declarative definitions, which require no programming knowledge and no code to be written.

Instead, those definitions are constructed using a simple, hierarchical structure expressed as e.g. a YAML file, similar to those used by tools that allow such sets to be deployed either locally or on common cloud providers, e.g. `docker-compose` or `terraform`.

The model and the schema used are documented in:

{% embed url="https://github.com/golemfactory/golem-architecture/blob/stranger80/GAP/golem_compose/gaps/gap-16_golem_compose/gap-16_golem_compose.md" %}


### Dapp-runner

Dapp-runner is an initial, reference implementation that allows applications defined as Golem dApps to be deployed and maintained on the Golem network. It takes one or more application descriptors expressed as YAML files, constructs the desired dApp model for such an application and executes all operations needed for the services constituting the app to be successfully deployed on Golem.

{% embed url="https://github.com/golemfactory/dapp-runner/" %}

### Dapp-manager

Dapp-manager is a simple CLI tool used to manage and run several separate instances of the `dapp-runner`. So, whereas `dapp-runner` ’s sole responsibility is deployment of a single application, `dapp-manager` can facilitate running several applications and easily monitoring their states using a simple command-line interface.

{% embed url="https://github.com/golemfactory/dapp-manager/" %}

### The Requestor Portal

The Requestor Portal ([portal.golem.network](http://portal.golem.network)) is Golem’s showcase website, allowing external users to run demo applications on Golem through a simple web interface without having to run Golem nodes themselves.

It utilizes `dapp-runner` and `dapp-manager` under the hood to orchestrate and interact with those deployments.

{% embed url="https://portal.golem.network/" %}
