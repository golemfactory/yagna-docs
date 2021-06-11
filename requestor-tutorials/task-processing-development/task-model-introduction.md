---
description: Overview of a typical Golem task application.
---

# Introduction to the task model

## How do I start?

{% hint style="info" %}
This example uses the standard VM runtime.
{% endhint %}

First, you need to think about your computational problem in terms of parallel execution. Let's visualize your computational problem:

![](../../.gitbook/assets/tutorial-01.jpg)

Next, you need to find a way how to divide the whole problem into fragments. Each fragment is a distinct part of the whole and may be processed by a different provider, independently from other fragments:

![](../../.gitbook/assets/tutorial-02.jpg)

In order to proceed further, you'll be required to design your app in such a way that it's able to:

1. Translate the problem fragments into input and output files the processing of which is performed independently in each of the providers.
2. Combine all the output files into the final solution of the problem at hand.

## What do I need to create a VM application for Golem?

When it comes to the implementation itself, any VM-based application for Golem is made up of two components:

1. a Docker image that will run as a container on providers.
2. Requestor agent - a piece of Python / JavaScript / TypeScript code that will execute the problem-dividing logic, orchestrate the execution on providers, and finally combine the output files to get the result for the whole problem.

{% hint style="success" %}
Now you know what a Golem VM application is and how it works.
{% endhint %}

Let's see how the implementation goes then! But first, let's understand how `hashcat`, the password-recovery tool which we are going to use, can be made to work in parallel.

