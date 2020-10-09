# Golem application - how to

## What is the Golem application?

Golem application is just some docker containers \(Providers\) that are orchestrated by Python or JavaScript code \(Requestor\). The orchestration is realized as three types of actions: 

* sending input files to the docker container
* running commands on the container
* getting output files from the container 

![](../../.gitbook/assets/image%20%281%29.png)

## How does Golem application work?

Currently, Golem network supports the following application architecture:

* Application is divided into two parts:
  * **Requestor** \(sometimes called _a_ _master node_\). Divides the computation problem into several parts, and send them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
  * **Provider** \(sometimes called _worker node_\). Executes the given part and returns results to the requestor.
* The Provider side execution is implemented as the docker container.
* The application creator prepares a dedicated dockerfile that describes the image. 
  * _If there \(for example on the docker hub\) exist image that can be used directly, there is no need to create a custom image._
* The application starting point is the Requestor side, which runs the requestor agent.
* The requestor agent gets the providers that meet its needs \(for example having enough RAM\) from the Golem's market. 
* The providers are asked to load the appropriate image. 
  * _If this is a subsequent run of the image, the image could already be cached by some of the providers._ 
* For each of the providers, the requestor prepared input data. Those are sent from the memory or local requestor's file system into the docker container's file system.
* One or several commands are executed on the provider's docker containers.
  * _It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor._
* Requestor transfers needed files from the provider's docker container's file systems to local file system.
* Requestor combines all the data transferred from providers to form final output that can be consumed by the application user.

Some additional details can be found here:

{% page-ref page="../../introduction/golems-details.md" %}

## What do you need to create Golem application?

