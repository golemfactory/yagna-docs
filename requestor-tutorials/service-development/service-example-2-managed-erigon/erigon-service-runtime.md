# Erigon Service runtime

## Runtime implementation

Here we demonstrate how self-contained ExeUnit runtimes can be implemented, tested and finally plugged into the Provider's daemon.

{% hint style="warning" %}
Please be aware that a custom runtime in this tutorial doesn't provide the level of isolation comparable with a virtual machine. It's just an executable running with the same privileges as the yagna daemon.
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

Now in the `deploy` we access `data_dir` property of `ErigonConf` struct from `Context` parameter `conf` property.

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

So the next part is to iterate through `Network`'s variant names and create a subdirectories for each of the networks.

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

Thanks to `ya-runtime-std` all that is left is to communicate success, by returning `Ok(None)` to the SDK.

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

During runtime startup the configuration file located in `$HOME/.local/share/ya-runtime-erigon/ya-runtime-erigon.json` is parsed and is initialising the instance of `ErigonConf` structure. If the file does not exist it will be created and initialized with default values during the first start of the runtime.

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

