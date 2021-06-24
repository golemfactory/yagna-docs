---
description: Ethereum client as a service, implemented as a self-contained runtime
---

# Service Example 2: Managed Erigon

The purpose of this example is to demonstrate building a Golem service using a dedicated, self-contained runtime. It features an Ethereum network client, Erigon (f.k.a. Turbo-geth) started on provider nodes on user's demand. Interaction with the service is *not* facilitated by Golem though.

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* Dedicated service runtime implemented with [ya-runtime-sdk](https://github.com/golemfactory/ya-runtime-sdk)
* Service management using [yapapi-service-manager](https://github.com/golemfactory/yapapi-service-manager)
{% endhint %}

{% hint style="info" %}
All code for this example can be found in this repository: [https://github.com/golemfactory/yagna-service-erigon/](https://github.com/golemfactory/yagna-service-erigon/)
{% endhint %}

## Architecture overview

![](erigon_architecture.jpg)

The application consist of three major components:

1. **User interface**  
   A browser-based interface written in TypeScript using [React](https://reactjs.org/). It allows the end user to interact with the application, i.e. start an Erigon node after authenticating with their [Metamask](https://metamask.io/) wallet, and later manage their node(s).
2. **Requestor server**  
   A Python application developed using [Quart](https://pgjones.gitlab.io/quart/) and [yapapi-service-manager](https://github.com/golemfactory/yapapi-service-manager). It acts both as an HTTP server handling requests from the user interface, and as a requestor agent submitting tasks to the Golem network.
3. **Erigon runtime**  
    A dedicated, self-contained runtime created with [ya-runtime-sdk](https://github.com/golemfactory/ya-runtime-sdk). It is a Rust binary wrapping [Erigon](https://github.com/ledgerwatch/erigon) service itself so that it can be orchestrated by yagna daemon. The runtime also controls the access to the service by managing [Nginx](https://www.nginx.com/) configuration.
   
A typical interaction flow proceeds in the following manner:

1. User opens the web interface in their browser.
2. User authenticates with their metamask wallet.
3. User clicks to start an Erigon node.
4. Request to start an Erigon node is sent via REST API to the requestor server.
5. Requestor starts a service activity (these steps are handled by `yagna` core and `yapapi` internally):
    1. Requestor server makes a number of API calls to the yagna daemon running on the requestor's machine in order to find an available Erigon provider and sign an agreement.
    2. Once the agreement is signed, requestor server sends a command to the provider to start an Erigon node.
    3. Yagna daemon running on the provider's machine spawns Erigon runtime process (a service wrapper/supervisor process).
8. Erigon runtime starts the actual Erigon service (backend & rpcdaemon processes).
9. Erigon runtime generates a new username and password and puts them in the NGINX configuration.
10. NGINX auto-reloads on configuration change, from now on granting access to the Erigon service only for user(s) authenticated with the newly created credentials. (NGINX is continuously running on provider's machine as a daemon, so it doesn't need to be started.)
11. The credentials are passed backed to the requestor server along with provider's node's public IP address and the port on which NGINX is listening.
12. Requestor server passes all the received information to the web interface where it can be viewed by the user.
13. User interacts with the Erigon service (via NGINX proxy).
14. Once the user finishes using their Erigon instance, they click to stop it.
15. Web interface sends request to stop the instance via REST API to the requestor server.
16. Requestor server sends a stop command to the provider.
17. Erigon runtime stops the Erigon service and exits.
18. Requestor server orchestrates payment for the service in the background without further user interaction.

{% hint style="info" %}
The design presented above excludes making any payments for the service by its end user. This omission was made intentionally to make te service implementation simpler. It's not a problem as long as the service is used for demonstrative purpose only.  
{% endhint %}

## Runtime implementation

## Requestor agent

## User interface

