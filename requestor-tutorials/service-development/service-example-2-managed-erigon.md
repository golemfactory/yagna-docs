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

* `url` - where our provider will be accepting requests
* `auth` - user/password pair that must be provided with each request
* `network` - Ethereum network name 

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

* We don't have any `image_hash` (contrary to the previouse examples) because we don't use a VM-based runtime
* We declare the runtime name, `erigon` - this must match the offered `exeunit-name` [TODO - link to provider offer description]
* `min_mem_gib` and `min_storage_gib` are used to filter out offers with to weak parameters (e.g. we would need more storage if we want to use mainnet than testnet)
  [TODO] - maybe remove those from the payload? They are necessary now to find any market offer, but blue says it might have disappared in yagna 0.7.1
  https://discord.com/channels/687954211702439971/828932441586532392/857201342291509248


#### Start

```python
async def start(self):
    #   startup - set start args (network parameter)
    self._ctx.deploy()
    start_args = await self._get_start_args()
    if start_args:
        erigon_init_args = start_args[0]
        erigon_init_args_str = json.dumps(erigon_init_args)
        self._ctx.start(erigon_init_args_str)
    else:
        self._ctx.start()

    #   Set url & auth
    self._ctx.run('STATUS')
    processing_future = yield self._ctx.commit()
    result = self._parse_status_result(processing_future.result())
    self.url, self.auth, self.network = result['url'], result['auth'], result['network']
```

Let's split that to separate parts.

##### Deploy command

```python
self._ctx.deploy()
```

This is the first thing that should always be done with `self._ctx`.

##### Determine start args

```
start_args = await self._get_start_args()
```

The runtime start accepts a single argument - a json with a single key `network` [TODO - link runtime section].
This `start_args` are defined by the final user (the one ordering Erigon service, e.g. via the web interface).

{% hint style="info" %}
Current `yapapi` has no pretty way of passing arguments to the `Service`, so this is implemented as a ugly-but-harmless hack:

```python
async def _get_start_args(self):
    while True:
        try:
            return self._cluster.instance_start_args
        except AttributeError:
            await asyncio.sleep(0.1)
```

This will be fixed in [the near future](https://github.com/golemfactory/yapapi/issues/372).
{% endhint %}


##### Start

```python
if start_args:
    erigon_init_args = start_args[0]
    erigon_init_args_str = json.dumps(erigon_init_args)
    self._ctx.start(erigon_init_args_str)
else:
    self._ctx.start()
```


`start_args` is expected to be a tuple, but there are no more assumptions - they are just passed here from the code that starts the service [TODO - link the appropriate further section].
Here we know that the runtime expects at most one argument (there is some default value) that is a `json`, so we dump the first argument to string (or start without any arguments if `start_args` are empty).
This could be also a good place to perform a requestor-side validation, we validate `start_arg` only in the runtime.

##### Perform a STATUS command

```python
self._ctx.run('STATUS')
```

[TODO]

#####  Fetch the results

```python
processing_future = yield self._ctx.commit()
result = self._parse_status_result(processing_future.result())
self.url, self.auth, self.network = result['url'], result['auth'], result['network']
```

```python
def _parse_status_result(self, raw_data: 'List[CommandExecuted]'):
   command_executed = raw_data[-1]

    erigon_data = command_executed.stdout
    erigon_data = json.loads(erigon_data)
    return erigon_data
```

[TODO]

#### run

There is no `run` function, because we use the one declared on `yapapi.Service` that just hangs forever.
[TODO]


### running the service with a simple script

...

### running the http erigon server

...

## User interface

