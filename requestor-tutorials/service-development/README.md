---
description: Running services on Golem
---

# Service Model development

Apart from the previously-supported task-based model described in the previous chapter, we're now presenting a **Services-based API** to allow the developers to define their own Golem services in a convenient way.

Theoretically, one can try using the task-based model to run services and the services model to run tasks as the models and their usage are not entirely disjoint. The reason why we decided to differentiate them is mostly for convenience and ease of use.

While the task-based API assumes that the developer starts with a problem that requires splitting into fragments in order to parallelize the execution using multiple providers, the services API assumes the user would like to treat provider nodes as something like service-hosting platforms, where each activity corresponds to a single instance of some service.

We have prepared a few articles to bet you well on your way to developing and running your own services on Golem.

First, some introduction is due to get you familiar with the concepts and assumptions we utilize in our high-level services API:

{% page-ref page="service-model-introduction.md" %}

Then, have a look at a minimal example of a service running on a Golem VM: 

{% page-ref page="service-example-0-hello-world.md" %}

And next, have a look at how a slightly more complicated service can be run on and interacted-with using Golem's Services API:

{% page-ref page="service-example-1-simple-service.md" %}

We'll be adding new examples here very soon, including one that will show you how to run services outside of a VM-based runtime using both the Requestor high-level SDK and the Provider SDK to wrap almost any external service as a Golem execution unit. Stay tuned! :\)

