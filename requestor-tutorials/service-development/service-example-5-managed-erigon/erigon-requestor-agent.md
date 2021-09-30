# Erigon Requestor agent

## Requestor agent

This part of the tutorial directly corresponds to the two previous requestor tutorials \([services hello world example]() and [simple service]()\). We have the same clear separation between service specification and service provisioning, but there are important differences:

* We use Erigon runtime instead of a VM-based runtime \(so we don't have any Dockerfile or `image_hash`\).
* We don't implement `async def run` - the service is only started/stopped, requestor is idle when the service it is running.
* We use [yapapi-service-manager](https://github.com/golemfactory/yapapi-service-manager) instead of pure `yapapi`.
* We integrate the requestor code with [Quart](https://pgjones.gitlab.io/quart/), a web framework.

### Service specification

As in previous tutorials, service specification is a subclass of `yapapi.Service`. Full code is available in the [yagna-erigon-repo](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/server/erigon_service.py), here we'll discuss the important parts.

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

* `url` - where Erigolem RPC \(running on the provider\) will be accepting requests
* `auth` - credentials that must be provided with each request
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
```

and used in `get_payload` in the service:

```python
@classmethod
async def get_payload(cls):
    return ErigonPayload()
```

Few important things to note here:

* We don't have any `image_hash` \(contrary to the previouse examples\) because we don't use a VM-based runtime.
* We declare the runtime name, `erigon` - this must match the offered [exeunit-name]().
* `min_mem_gib` - minimum amount of RAM the provider has to offer. This is pretty useless in the Erigon case \(contrary to the e.g. VM-based runtimes\), but is required because of a known `yapapi` [bug](https://github.com/golemfactory/yapapi/issues/500).

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

**Deploy**

```python
self._ctx.deploy()
```

This is the first thing that should always be done with `self._ctx`.

**Determine start args**

```python
start_args = await self._get_start_args()
```

`start_args` - in the erigon case - are a single-item tuple:

```python
(
    {'network': <ETHEREUM NETWORK NAME>},
)
```

These `start_args` are defined by the final user \(the one ordering Erigon service, e.g. via the web interface\) and passed directly to the runtime.

{% hint style="info" %}
Current `yapapi` has no pretty way of passing arguments to the `Service`, so this is implemented as an ugly-but-harmless hack:

```python
async def _get_start_args(self):
    while True:
        try:
            return self._cluster.instance_start_args
        except AttributeError:
            await asyncio.sleep(0.1)
```

This will be addressed in [the near future](https://github.com/golemfactory/yapapi/issues/372).
{% endhint %}

**Start**

```python
if start_args:
    erigon_init_args = start_args[0]
    erigon_init_args_str = json.dumps(erigon_init_args)
    self._ctx.start(erigon_init_args_str)
else:
    self._ctx.start()
```

`start_args` is expected to be a tuple, but there are no more assumptions - they are just passed here from the [code that starts the service](). The Erigon runtime expects at most one argument and it is expected to be a `json`, so we send the serialized first argument \(or start without any arguments if `start_args` are empty\). This could be also a good place to perform a requestor-side validation, we validate `start_arg` only in the runtime.

**Perform a STATUS command**

```python
self._ctx.run('STATUS')
```

Run a command 'STATUS'. Actually, we could send anything other than `STATUS` - our runtime ignores the command and does always the same thing - returns running erigon url, credentials and Ethereum's network.

{% hint style="info" %}
Compare this to VM-based commands, like

```python
self._ctx.run('/bin/date')
self._ctx.run('/bin/sh', '-c', 'cat some_file.txt')
```

etc.

In the VM environment, available commands are defined in the image and they usually default to commands available in the base linux image + optional additional commands, like `/golem/run/simple_service.py` in the [simple service](). When using a custom runtime, we are free to implement any commands we want - but also we have no built-in commands, not even `ls`.
{% endhint %}

**Fetch the results**

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

STATUS command executed in the runtime returns JSON-serialized data. On the requestor side it is available in `stdout` of the appropriate `command_executed`.

{% hint style="info" %}
`processing_future.results()` is a list of CommandExecuted objects - one per each command. In our case, there are three : `deploy`, `start`, and `run(STATUS)`, and we are interested only in the output of the last one.
{% endhint %}

#### Run & shutdown

We don't need to implement those functions because the default `yapapi.Service` implementation is exactly what we want:

* Default `run()` waits forever.
* Default `shutdown()` terminates the agreement. We don't have to perform any additional cleanup - it is already implemented in the runtime \(e.g. erigon process is stopped\).

### Running the HTTP Erigon server

We implement an HTTP server that responds to 3 requests:

* `createInstance` - start a new erigon,
* `stopInstance/<id>` - stop this erigon,
* `getInstances` - list all current & past erigons.

There is also some basic authentication - the only user who can see/stop an erigon is the one who created it. We use the [Quart](https://pgjones.gitlab.io/quart/) framework.

{% hint style="info" %}
Code that uses `yapapi` must be called in an asynchronous context. Quart is an `async` equivalent of the much more popular [Flask](https://flask.palletsprojects.com/en/2.0.x/).
{% endhint %}

Full server code is [here](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/server/app.py), only Golem-related part will be discussed in this tutorial.

For the documentation on `yapapi-service-manager` check [README](https://github.com/golemfactory/yapapi-service-manager).

#### Configuration

\([run\_server.py](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/run_server.py)\)

```python
app.yapapi_executor_config = {
    'budget': 10,
    'subnet_tag': os.environ.get('SUBNET_TAG', 'erigon'),
}
```

Here we define the `yapapi.Golem` [init\_args](https://handbook.golem.network/yapapi/api-reference#_engine-objects). `app.yapapi_executor_config` is passed directly to the `Golem` object.

#### Start/stop the requestor

```python
from yapapi_service_manager import ServiceManager

@app.before_serving
async def start_service_manager():
    app.service_manager = ServiceManager(app.yapapi_executor_config)


@app.after_serving
async def close_service_manager():
    await app.service_manager.close()
```

We initialize the ServiceManager during the server startup and close it when the server exits. This is \(roughly\) equivalent to entering/exiting `async with Golem`.

{% hint style="warning" %}
There is no state preserved outside of the process memory, so when using a generic WSGI server \(like `gunicorn`\) you shouldn't

* Start more than one worker,
* Use worker-recycling tools \(like `max_requests` in `gunicorn`\).
{% endhint %}

#### Create a new Erigon

```python
from .erigon_service import Erigon
from .erigon_service_wrapper import ErigonServiceWrapper

@app.route('/createInstance', methods=['POST'])
async def create_instance():
    request_data, user_id, init_params = [some_non_golem_stuff]

    erigon = app.service_manager.create_service(Erigon, (init_params,), ErigonServiceWrapper)

    erigon.name = request_data.get('name', f'erigon_{erigon.id}')
    app.user_erigons[user_id][erigon.id] = erigon

    return erigon.api_repr(), 201
```

First, we extract `request_data`, `user_id` and `init_params` from the request, this is done in a pretty standard `Quart`ish way.

Then comes the most important line:

```python
erigon = app.service_manager.create_service(Erigon, [init_params], ErigonServiceWrapper)
```

`Erigon` is the `yapapi.Service`-based class we implemented in the [previous section]().

`init_params` is a dictionary `{'network': <ETHEREUM-NETWORK-NAME>}` that is defined in the request.

`ErigonServiceWrapper` is a class extending `yapapi-service-manager.ServiceWrapper` that can be found [here](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/server/erigon_service_wrapper.py). It is neither very important nor interesting: we just need a place to store and access some additional erigon-specific information, like `created_at` timestamp or `name`. This could be implemented in many different ways, but this is the most convenient - the returned `erigon` object \(an instance of `ErigonServiceWrapper`\) encapsulates all of the logic and has exactly the interface we need:

```python
erigon.name         # user-defined name
erigon.api_repr()   # representation of the erigon, sent to the frontend
erigon.stop()       # stops the service (service starts when the object is created)
```

In the next three lines:

```python
erigon.name = request_data.get('name', f'erigon_{erigon.id}')
app.user_erigons[user_id][erigon.id] = erigon
return erigon.api_repr(), 201
```

We set the Erigon name, save the information about newly created Erigon, and send its representation as a response.

#### Stop the erigon

```python
@app.route('/stopInstance/<erigon_id>', methods=['POST'])
async def stop_instance(erigon_id):
    user_id = get_user_id()

    try:
        erigon = app.user_erigons[user_id][erigon_id]
    except KeyError:
        return 'Invalid erigon_id', 404

    erigon.stop()

    return erigon.api_repr(), 200
```

Nothing really interesting here, we just:

* Extract the `user_id` from the request
* Check if this is the user who created this Erigon \(compare the `app.user_erigons[user_id][erigon.id] = erigon` line in the previous section\),
* Stop the Erigon - this _initializes_ the stopping process, it is not stopped immediately \(because stopping needs some action on the provider side\),
* Return Erigon representation as a response.

#### Get all user's Erigons

```python
@app.route('/getInstances', methods=['GET'])
async def get_instances():
    user_id = get_user_id()
    erigons = app.user_erigons[user_id].values()
    data = [erigon.api_repr() for erigon in erigons]
    return json.dumps(data), 200
```

We select all Erigons created by the user and return their representation.

### Running the service with a simple script

There is also a [simple script that just starts the erigon services](https://github.com/golemfactory/yagna-service-erigon/blob/master/requestor/run_erigon_service.py). Service is running forever, status is printed every second, ctrl+C leads to a graceful shutdown. This is just a development tool, similar to [yapapi-service-manager examples](https://github.com/golemfactory/yapapi-service-manager/tree/master/examples).

