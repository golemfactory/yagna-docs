---
description: JS API introduction
---

# JS API Levels

## Introduction

The golem JavaScript library provides developers with two levels of abstraction for interacting with the golem:

- **High Level** - This level allows developers to interact with the golem with minimal knowledge of the golem's internal components. It is designed to be simple and easy to use.

{% content-ref url="./high-level/introduction.md" %}
[Create your own task application using High-level API](./high-level/introduction.md)
{% endcontent-ref %}

- **Mid Level** - This level allows developers to use the library for more complex cases, and it requires knowledge of the golem's component architecture. It provides more fine-grained control over the golem's functionality.

{% content-ref url="./mid-level/introduction.md" %}
[Create your own task application using Mid-level API](./mid-level/introduction.md)
{% endcontent-ref %}

The following diagram illustrates the division of the individual parts of the golem:

![Golem Component Architecture](golem-component-architecture.png)

The High Level API provides an easy-to-use interface to the core functionality of the golem, such as creating and managing tasks with only a few lines of code.
The Mid Level API gives developers access to the Golem-specific components, such as the Demand that is published on the market or Offer that is received from the provider, for more advanced use cases.

Choose the level of abstraction that best suits your needs and follow the links provided to learn more about each level and its capabilities.
