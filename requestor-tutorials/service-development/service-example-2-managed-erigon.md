---
description: 'Ethereum client as a service, implemented using a self-contained runtime'
---

# Service Example 2: Erigolem – Managed Erigon

The purpose of this example is to demonstrate building a Golem service using a dedicated, self-contained runtime. It features an Ethereum network client, Erigon \(f.k.a. Turbo-geth\) started on provider nodes on user's demand. Interaction with the service, once it's running and its location and credentials have been passed to the requestor, is _not_ facilitated by Golem though.

{% hint style="info" %}
This example illustrates the following Golem features & aspects:

* Dedicated service runtime implemented with [ya-runtime-sdk](https://github.com/golemfactory/ya-runtime-sdk)
* Service management using [yapapi-service-manager](https://github.com/golemfactory/yapapi-service-manager)
{% endhint %}

{% hint style="info" %}
All code for this example can be found in this repository: [https://github.com/golemfactory/yagna-service-erigon/](https://github.com/golemfactory/yagna-service-erigon/)
{% endhint %}

## Architecture overview

![](../../.gitbook/assets/erigon_architecture.jpg)

The application consists of three major components:

1. **User interface**

   A browser-based interface written in TypeScript using [React](https://reactjs.org/). It allows the end user to interact with the application, i.e. start an Erigon node after authenticating with their [Metamask](https://metamask.io/) wallet, and later to manage their node\(s\).

2. **Requestor server**

   A Python application developed using [Quart](https://pgjones.gitlab.io/quart/) and [yapapi-service-manager](https://github.com/golemfactory/yapapi-service-manager). It acts both as an HTTP server \(handling requests from the user interface\), and as a requestor agent \(submitting tasks to the Golem network\).

3. **Erigon runtime**

   A dedicated, self-contained runtime created with [ya-runtime-sdk](https://github.com/golemfactory/ya-runtime-sdk). It is a Rust binary wrapping [Erigon](https://github.com/ledgerwatch/erigon) service itself so that it can be orchestrated by the yagna daemon. The runtime also controls the access to the service by managing [Nginx](https://www.nginx.com/) configuration.

A typical interaction flow proceeds in the following manner:

1. User opens the web interface in their browser.
2. User authenticates with their metamask wallet.
3. User clicks to start an Erigon node.
4. Request to start an Erigon node is sent via the REST API to the requestor server.
5. Requestor starts a service activity \(these steps are handled by `yagna` core and `yapapi` internally\):
   1. Requestor server makes a number of API calls to the yagna daemon running on the requestor's machine in order to find an available Erigon provider and sign an agreement.
   2. Once the agreement is signed, requestor server sends a command to the provider to start an Erigon node.
   3. Yagna daemon running on the provider's machine spawns an Erigon runtime process \(a service wrapper/supervisor process\).
6. Erigon runtime starts the actual Erigon service \(backend & rpcdaemon processes\).
7. Erigon runtime generates a new username and password and puts them in the NGINX configuration.
8. NGINX auto-reloads on configuration change, from now on granting access to the Erigon service only for user\(s\) authenticated with the newly-created credentials. \(NGINX is continuously running on provider's machine as a daemon, so it doesn't need to be started.\)
9. The credentials are passed backed to the requestor server along with provider's node's public IP address and the port on which NGINX is listening.
10. Requestor server passes all the received information to the web interface where it can be viewed by the user.
11. User interacts with the Erigon service \(via NGINX proxy\).
12. Once the user finishes using their Erigon instance, they click to stop it.
13. Web interface sends a request to stop the instance via the REST API to the requestor server.
14. Requestor server sends a stop command to the provider.
15. Erigon runtime stops the Erigon service and exits.
16. Requestor server orchestrates a payment for the service in the background without further user interaction.

{% hint style="info" %}
The design presented above excludes making any payments for the service by its end user. This omission was made intentionally to make te service implementation simpler. It's not a problem as long as the service is used for demonstrative purpose only.
{% endhint %}

## Runtime implementation

Here we demonstrate how self-contained Exe-Unit runtimes can be implemented, tested and finally plugged into the Provider's daemon.

{% hint style="warning" %}
Please be aware that a custom runtime doesn't provide the level of isolation comparable with a virtual machine. It's just an executable running with the same privileges as the yagna daemon.
{% endhint %}

### Erigon runtime

First, let's discuss what the purpose of the Erigon runtime is to gain some high-level overview. The runtime:

* Accepts an Ethereum network's name \(e.g. 'mainnet' or 'rinkeby'\) from the requestor agent,
* Starts Erigon binaries to sync with the chosen network and serve Erigon RPC endpoint,
* Generates credentials for basic authentication which is implemented with nginx,
* Returns the credentials to the requestor agent so the user of the service can connect to the Erigon RPC.

Please refer to the "Provider's node" in the above Architecture overview diagram.

### Implementation

{% hint style="info" %}
Before diving into this section you might want to review simpler [example runtime](https://github.com/golemfactory/ya-runtime-sdk/blob/main/examples/example-runtime/src/main.rs) available in the [ya-runtime-sdk](https://github.com/golemfactory/ya-runtime-sdk/) repository.
{% endhint %}

Erigon runtime declares two structures

* `ErigonConf` - containing runtime configuration with default values,
* `ErigonRuntime` - derives from `RuntimeDef` implements the required methods from `ya-runtime-sdk::Runtime` trait

At least these methods from the `Runtime` trait have to be implemented but [Runtime SDK](https://github.com/golemfactory/ya-runtime-sdk/) provides default implementation to several others.

#### Deploy

{% hint style="info" %}
**deploy** - It's run only once per activity, does not accept parameters \(but there are plans to add them in the future release\), return value is not passed to the requestor agent. Requestor agent is not required to call `deploy` directly, in this case `deploy` and `start` will be called automatically by the SDK before the first command sent to the runtime.
{% endhint %}

In the Erigon runtime this method asserts that parent directory for Erigon data provided via the configuration exists and then creates directories for each Ethereum network supported by the service.

Let's go through it step by step

Service configuration struct is defined as follows, see the `data_dir` property below.

```rust
#[derive(Deserialize, Serialize)]
pub struct ErigonConf {
    public_addr: String,
    data_dir: String,
    passwd_tool_path: String,
    // ...
}
```

We were able to declare most properties with the type of `String` not `Option<String>` because we also implemented the `Default` trait for `ErigonConf` struct.

Now in the `deploy` we access `data_dir` property of `EriginConf` struct from `Context` parameter `conf` property.

```rust
fn deploy<'a>(&mut self, ctx: &mut Context<Self>) -> OutputResponse<'a> {
    let data_dir = PathBuf::from(&ctx.conf.data_dir);

    // check if parent data directory exists
    if !(data_dir.exists() && data_dir.is_dir()) {
        panic!("Configuration 'data_dir' directory has to exists...");
    }
```

We declared supported networks of the Ethereum in the `Network` enum

```rust
custom_derive! {
#[derive(Debug, PartialEq, EnumDisplay, EnumFromStr, IterVariantNames(NetworkVariantNames))]
pub enum Network {
    Goerli,
    Rinkeby,
    Ropsten,
}}
```

So the next part is to iterate through `Network`'s variant names and create a subdirectories for each of the network.

```rust
    // create all supported chains data subdirs
    for chain_subdir in Network::iter_variant_names()
                            .map(|chain| chain_subdir(data_dir.as_path(), chain)) {
        if !&chain_subdir.is_dir() {
            fs::create_dir(&chain_subdir)
                .unwrap_or_else(|_| panic!("Unable to create subdir {:?}", &chain_subdir));
        }
    }
```

Thanks to `ya-runtime-std` all is left is to communicate success, by returning `Ok(None)` to the SDK.

#### Start

{% hint style="info" %}
**start** - called after `deploy` usually once per activity, accepts parameters. Analogically with `deploy` if not run explicitly via the SDK `deploy` and `start` without parameters are run in order before any command is send to the runtime.
{% endhint %}

In the Erigon runtime we use `start` method to receive the `network` parameter from the requestor, start Erigon's binaries and generate new credentials for nginx basic auth. As above, we'll review the code more deeply.

First, we receive the input from the caller from context `ctx.cli.command.args()` provided by SDK's `CommandCLI` trait `Command` enum. Arguments to start are passed as a `&Vec<String>`, we're interested only of the first of them. `get_chain_from_config` is retrieving the network value from the json and converts it to the `Network` variant, to assert it's within supported networks. We're also setting its lowercased String value in the `erigon_chain` property for the later use.

```rust
fn start<'a>(&mut self, ctx: &mut Context<Self>) -> OutputResponse<'a> {
    let chain = get_chain_from_config(ctx.cli.command.args().into_iter().next());
    let chain = chain.to_string().to_lowercase();
    self.erigon_chain = Some(chain.clone());
```

Next, we're generating new password for the nginx's basic auth. We're generating random string, set it with the `passwd_tool` and store it in the `erigon_password` service's property.

```rust
// Generate user & password entry with passwd tool
    let rng = thread_rng();
    let password: String = rng.sample_iter(Alphanumeric)
        // ...
        .collect();

    let _ = generate_password_file(
        &ctx.conf.passwd_tool_path,
        &ctx.conf.passwd_file_path,
        &password,
    )
    .expect("Unable to create passwd file");
    self.erigon_password = Some(password);
```

What's left is to spawn `erigon` and `rpcdaemon` processes and store handles to them so we can kill them when the service will be stopped.

```rust
    let mut erigon_pid = spawn_process(
        &mut Command::new(&path.join(ERIGON_BIN))
            .arg("--chain")
            .arg(&chain),
        &data_dir,
        &[""; 0],
    )
    .expect("Erigon: Failed to spawn");

    let rpcd_pid = spawn_process(...);

    self.erigon_pid = Some(erigon_pid);
    self.rpcdaemon_pid = Some(rpcd_pid);
```

The `start`'s return value is serving only troubleshooting purposes as the Erigon agent ignores it but it can be reviewed in the debugger session.

{% hint style="info" %}
Note that the difference between `deploy` and `start` regarding the Erigon runtime might not be obvious. It's easier to think of them in terms of VM runtimes where `deploy` is needed for runtime preparation, e.g. download the image, after `start` runtime should be ready to run the commands.
{% endhint %}

#### Run command

{% hint style="info" %}
**run\_command** - called every time the corresponding agent SDK [`run`](runhttps://github.com/golemfactory/yagna-docs/blob/master/yapapi/api-reference.md#run) is called on the `WorkContext` object. Result can be obtained from the `WorkContext`'s results array after sequence of commands is executed by `commit`.
{% endhint %}

In the Erigon runtime this method is used to provide Erigon service's credentials to the agent. Here we're just forming the JSON string response and passing it as a command output, see the call of `run_ctx.stdout(...)` below.

```rust
    let erigon_status_data = serialize::json::json!({
        "url": &ctx.conf.public_addr,
        // ...
    });

    ctx.command(|mut run_ctx| async move {
        let stdout = format!("{}", erigon_status_data);
        run_ctx.stdout(stdout).await;
        Ok(())
    })
```

#### Stop

{% hint style="info" %}
**stop** - can be called explicitly by the requestor agent or automatically due to agreement termination.
{% endhint %}

In the Erigon runtime `stop` method is used to kill Erigon processes started in `start`.

```rust
    let erigon_kill_ok = match &mut self.erigon_pid {
        Some(erigon_pid) => erigon_pid.kill().is_ok(),
        None => false,
    };

    // kill rpc_daemon process bellow
```

### Extentions

Above methods corresponds to [`CLI::Command` enum](https://github.com/golemfactory/ya-runtime-sdk/blob/main/ya-runtime-sdk/src/cli.rs#L11). One can extend the default `CLI` by

* Deriving `StructOpt` on the `CLI` struct,
* Decorating the runtime struct with `#[cli(<struct_name>)]`.

Custom CLI arguments will be passed to each command by `runtime::Context`.

Default [`RuntimeMode`](https://github.com/golemfactory/ya-runtime-sdk/blob/4be7534b61cd47ab8d1764d6fd840480744dbfba/ya-runtime-sdk/src/runtime.rs#L73) is `Server`. In this mode runtime is deployed and then communicates with the `ExeUnit` via the `Runtime` API. Another option is `RuntimeMode::Command` where each command is a separate invocation of the runtime binary.

### Runtime configuration

During runtime startup the configuration file located in `$HOME/.local/share/ya-runtime-erigon/ya-runtime-erigon.json` is parsed and is initialising the instance of `ErigonConf` structure. If the file does not exists it will be created and initialized with default values during the first start of the runtime.

#### Example configuration file

```javascript
{
  "public_addr": "https://0.erigon.golem.network:8545",
  "data_dir": "/data/erigon",
  "passwd_tool_path": "htpasswd",
  "passwd_file_path": "/etc/nginx/erigon_htpasswd",
  "password_default_length": 15,
  "erigon_http_addr": "127.0.0.1",
  "erigon_http_port": "8555"
}
```

### Testing the runtime

Once needed SDK methods are implemented we can give our runtime a try in the [debugger](https://github.com/golemfactory/ya-runtime-dbg/). For example our Erigon runtime can be executed in the debugger shell running the following command.

```bash
ya-ya-runtime-dbg \
  --runtime ./target/debug/ya-runtime-erigon \
  --workdir ./target/debug \
  --start-arg '{"network": "goerli"}'
```

{% hint style="info" %}
Please mind it requires Erigon binaries present in the same directory \(all needed binaries for Ubuntu Linux can be downloaded from the [binary release](https://github.com/golemfactory/yagna-service-erigon/releases/tag/ya-runtime-erigon-v0.1.0)\). Also `htpasswd` from the `apache-tools` is needed to be present in the `PATH` but for the local testing you can mock it with `echo` changing configuration file property `"passwd_tool_path": "echo",`
{% endhint %}

### Pluging the runtime into `golemsp`

In the `$HOME/.local/lib/yagna/plugins/` directory create

* file `ya-runtime-erigon.json` where you describe the plugin

  ```javascript
  [
  {
    "name": "erigon",
    "version": "0.1.0",
    "supervisor-path": "exe-unit",
    "runtime-path": "ya-runtime-erigon/ya-runtime-erigon",
    "description": "Service wrapper for Erigon (formelly Turbo-Geth)",
    "extra-args": ["--runtime-managed-image"]
  }
  ]
  ```

* directory `ya-runtime-erigon` \(compare `runtime-path` in above file\) where `ya-runtime-erigon` binary along with Erigon binaries are placed.

New runtime needs also to be enabled in `$HOME/.local/share/ya-provider/presets.json`. Preset object can be copied from other presets. Please note that `exeunit-name` has to match to the `name` property of the plugin above

```javascript
{
  "active": [
    "erigon",
    ...
  ],
  "presets": [
    {
      "name": "erigon",
      "exeunit-name": "erigon",
      "pricing-model": "linear",
      "usage-coeffs": { ... }
    },
```

## Requestor agent

This part of the tutorial directly corresponds to the two previous requestor tutorials \([services hello world example](service-example-0-hello-world.md) and [simple service](service-example-1-simple-service.md)\). We have the same clear separation between service specification and service provisioning, but there are important differences:

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
* We declare the runtime name, `erigon` - this must match the offered [exeunit-name](service-example-2-managed-erigon.md#pluging-the-runtime-into-golemsp).
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

`start_args` is expected to be a tuple, but there are no more assumptions - they are just passed here from the [code that starts the service](service-example-2-managed-erigon.md#create-a-new-erigon). The Erigon runtime expects at most one argument and it is expected to be a `json`, so we send the serialized first argument \(or start without any arguments if `start_args` are empty\). This could be also a good place to perform a requestor-side validation, we validate `start_arg` only in the runtime.

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

In the VM environment, available commands are defined in the image and they usually default to commands available in the base linux image + optional additional commands, like `/golem/run/simple_service.py` in the [simple service](service-example-1-simple-service.md). When using a custom runtime, we are free to implement any commands we want - but also we have no built-in commands, not even `ls`.
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

`Erigon` is the `yapapi.Service`-based class we implemented in the [previous section](service-example-2-managed-erigon.md#service-specification).

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

## Becoming an Erigolem provider

Here we describe an [installation script](https://github.com/golemfactory/yagna-service-erigon/blob/master/install_provider.sh) which should make the whole process of becoming an Erigolem provider fun and smooth. The script is prepared for Ubuntu 18.04 or later and should work on other Linux distributions after some modifications.

{% hint style="warning" %}
This is an experimental setup. It's not intended to be run on personal computers because:

* It creates a separate user which will run the provider daemon,
* It installs the NGINX web server and certbot,
* Optionally, it generates a Let's Encrypt certificate and sets certbot to remind you about certificate renewals,
* It _disables all runtimes_ for yagna other than `ya-runtime-erigon`.
{% endhint %}

### Requirements

* Ubuntu 18.04 or later
* Root privileges
* Public IP address or a DNS name
* Ability to open a port for the Erigon service

{% hint style="info" %}
By default nginx's reverse-proxy is listening on the standard Erigon port `8545`. You need to open this port for incoming traffic. If you wish your Erigolem service to be available on a different port number \(e.g. because `8545` cannot be opened\), you need to edit the installation script.
{% endhint %}

Example patch changing `8545` to `9999`

```diff
diff --git a/install_provider.sh b/install_provider.sh
index 2bb4de9..41ad5e2 100644
--- a/install_provider.sh
+++ b/install_provider.sh
@@ -161,8 +161,8 @@ http {

     # example.com
     server {
-        listen                               8545${ERIGON_USE_SSL:+ ssl http2};
-        listen                               [::]:8545${ERIGON_USE_SSL:+ ssl http2};
+        listen                               9999${ERIGON_USE_SSL:+ ssl http2};
+        listen                               [::]:9999${ERIGON_USE_SSL:+ ssl http2};
         server_name                          $ERIGON_HOSTNAME;

         ${ERIGON_USE_SSL:+# SSL}
@@ -240,7 +240,7 @@ mkdir -p "${ERIGON_USER_HOME}/.local/share/ya-runtime-erigon"

 cat >"${ERIGON_USER_HOME}/.local/share/ya-runtime-erigon/ya-runtime-erigon.json" <<EOF
 {
-  "public_addr": "https://${ERIGON_HOSTNAME}:8545",
+  "public_addr": "https://${ERIGON_HOSTNAME}:9999",
   "data_dir": "${ERIGON_DATADIR}",
   "passwd_tool_path": "htpasswd",
   "passwd_file_path": "/etc/nginx/erigon_htpasswd",
```

### Parameters for the script

Script behavior can be modified by the following environment variables:

| name | default value | description |
| :--- | ---: | :--- |
| ERIGON\_USER | `golem` | OS user the service is running on |
| ERIGON\_DATADIR | `/data/erigon` | Erigon data directory. Each chain data is collected in the subdirs |
| ERIGON\_HOSTNAME |  | **HAS TO** be set before running the installation script, e.g. `ERIGON_HOSTNAME=X.erigon.golem.network` |
| ERIGON\_DISABLE\_SSL |  | Test this script without nagging letsencrypt services. If not set, \(the inverse\) `ERIGON_USE_SSL` is set |
| ERIGON\_EMAIL |  | Not needed when `ERIGON_DISABLE_SSL` is set. Email address for the certbot to remind of SSL certificate renewal. |

### Running the script

1. **Download the installation script on the installation machine**

   ```bash
    curl -sSfL -o install_provider.sh \
        https://raw.githubusercontent.com/golemfactory/yagna-service-erigon/master/install_provider.sh
   ```

2. **Review and edit the script if needed**
3. **Execute the script**

   Example script invocation \(_provider values for your environment_\)

   ```bash
    sudo env ERIGON_USER=golem \
         ERIGON_HOSTNAME=ec2-54-74-210-145.eu-west-1.compute.amazonaws.com \
         ERIGON_DATADIR=/data/erigon \
         ERIGON_DISABLE_SSL=y \
    bash install_provider.sh
   ```

   During the installation you will be asked to:

   * Accept Golem's licence terms,
   * Provide the name for the provider node,
   * Provide the subnet the node will be subscribed to,
   * Provide your wallet address,
   * Provide the desired price per hour \(in GLM\).

4. **Make sure the port is opened**

   It depends on how your machine was provisioned, but you might need also to allow ingress connections on the firewall.

   ```bash
    sudo ufw allow 8545/tcp
   ```

### Check installation

After a successful installation, verify that the service is running.

```bash
sudo systemctl status golem
```

You can also check the logs of the running service

```bash
sudo journalctl -u golem -e
```

