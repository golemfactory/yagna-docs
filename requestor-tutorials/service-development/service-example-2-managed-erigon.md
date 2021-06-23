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

1.
2.
3. ...

## Runtime implementation

## Requestor agent

This part of the tutorial directly corresponds to the two previous requestor tutorials ([services hello world example](service-example-0-hello-world.md) and [simple service](service-example-1-simple-service.md)). It is split into [TODO]

### Service specification

As in previous tutorials, service specification is a subclass of `yapapi.Service`.
Full code is available in the [yagna-erigon-repo](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/server/erigon_service.py), here we'll discuss the important parts.

#### Initialization:

```python
class Erigon(Service):
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.url = None
        self.auth = None
        self.network = None
```

We add three attributes that are specific to our service logic:

* url - where our provider will be accepting requests
* auth - user/password pair that must be provided with each request
* network - Ethereum network name 

They are initialized to `None` and later - when the service starts - will be updated with the data acquired from the runtime.

{% hint style="info" %}
We have no control of the `Erigon` service class initialization, so the

```python
def __init__(self, *args, **kwargs):
    super().__init__(*args, **kwargs)
```

part is required.
{% endhint %}

#### Payload

The payload is defined in [ErigonPayload](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/server/erigon_payload.py) class:

```python
ERIGON_RUNTIME_NAME = "erigon"

@dataclass
class ErigonPayload(Payload):
    runtime: str = constraint(inf.INF_RUNTIME_NAME, "=", ERIGON_RUNTIME_NAME)
    min_mem_gib: float = constraint(inf.INF_MEM, ">=", 0.5)
    min_storage_gib: float = constraint(inf.INF_STORAGE, ">=", 0.5)
```

and used this way in the service:

```python
@classmethod
async def get_payload(cls):
    return ErigonPayload()
```

Few important things to note here:

* we don't have any `image_hash` (contrary to previouse examples) because we don't use a VM-based runtime
* we declare the runtime name, `erigon` - this must match the offered `exeunit-name` [TODO - link to provider offer description]
* `min_mem_gib` and `min_storage_gib` are used to filter out offers with to weak parameters (e.g. we would need more storage if we want to use mainnet than testnet)

## User interface

