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

As the role of the provider is to serve IT resources, the actual provider agent logic is pretty universal to all the business cases. This is why we provide provider binaries as a pre-build Linux installation package.

![Golem deamon and the agents. Components to be developed by 3rd party marked yellow.](../.gitbook/assets/requestor-tutorial-details%20%281%29.png)

When building a product on Golem, there two areas that require custom development \(market yellow on the above diagram\):

* **Requestor agent**

Defines the resource demands and orchestrates the task execution

* **Docker image**

Defines the actual code that performs the tasks on the provider's hardware

## Being requestor and provider at the same time

{% hint style="info" %}
 Golem daemon can act as requestor and provider at the same time.
{% endhint %}

Although the Golem code base allows Golem demon to act as a requestor and provider at the same time, we currently do not support this scenario configuration by any dedicated tutorials.

