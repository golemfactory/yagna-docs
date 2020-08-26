---
description: Internal details
---

# Golem's details

{% hint style="danger" %}
This documentation section is under development.
{% endhint %}

## Golem daemon and the agents

The Golem is defined mainly by the Golem network protocol.

{% hint style="info" %}
Golem daemon is the default implementation of the Golem network protocol.
{% endhint %}

The same Golem daemon binary is used both by the requestor and provider.

{% hint style="info" %}
The difference between requestor and provider is the use of requestor or provider agent.
{% endhint %}

As the role of the provider is to serve IT resources, the actual provider agent logic is universal to all business cases. This is why we provide provider binaries as a pre-built Linux installation package.

![](../.gitbook/assets/tnm-docs-infographics-07.jpg)

When building a product on Golem, there are two areas that require custom development \(marked with dark blue background on the diagram above\):

* **Requestor agent**

Defines the resource demands and orchestrates the task execution

* **Docker image**

Defines the actual code that performs the tasks on the provider's hardware

## Being requestor and provider at the same time

{% hint style="info" %}
Golem daemon can act as requestor and provider at the same time.
{% endhint %}

Although the Golem code base allows Golem demon to act as a requestor and provider at the same time, we currently do not support this scenario configuration by any dedicated tutorials.

