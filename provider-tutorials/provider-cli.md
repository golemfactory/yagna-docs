---
description: Golem Provider Command Line Interface
---

# Provider CLI reference

{% hint style="info" %}
Keep in mind that that is a really basic release, and future updates will give you much more options to play with.
{% endhint %}

## CLI commands

Run `golemsp help` without arguments to see top-level usage information:

```css
$ golemsp help
golemsp 0.10.1 (6ae8c21a 2022-06-06 build #223)
User friedly CLI for running Golem Provider

USAGE:
    golemsp <SUBCOMMAND>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    run         Run the golem provider
    stop        Stop the golem provider
    settings    Manage settings
    status      Show provider status
    help        Prints this message or the help of the given subcommand(s)
```

### Run

`golemsp run` - Start the Golem provider. It uses `mainnet` as a payment platform by default.

Invoke `golemsp run --help` to see more options.

### Settings

```css
$ golemsp settings
golemsp-settings 0.2.0
Manage settings

USAGE:
    golemsp settings <SUBCOMMAND>

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

SUBCOMMANDS:
    set     Change settings
    show    Show current settings
    help    Prints this message or the help of the given subcommand(s)
```

#### Settings set

`golemsp settings set --help` - to see how to change settings. Invoking this will prompt usage, flags, and options.

example

```css
$ golemsp settings set --help
golemsp-settings-set 0.2.0
Change settings

USAGE:
    golemsp settings set [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
        --node-name <node-name>
        --cores <num>                       Number of shared CPU cores
        --memory <bytes (like "1.5GiB")>    Size of shared RAM
        --disk <bytes (like "1.5GiB")>      Size of shared disk space
        --starting-fee <GLM (float)>        Price for starting a task
        --env-per-hour <GLM (float)>        Price for working environment per hour
        --cpu-per-hour <GLM (float)>        Price for CPU per hour
        --account <account>                 Account for payments [env: YA_ACCOUNT=]
        --payment-network <networks>...     Payment network [env: YA_PAYMENT_NETWORK=]  [default: mainnet]
					    [possible values: mainnet, rinkeby, goerli,
					    polygon, mumbai]
```

In order to change a particular setting \(for eg. price settings\) type:

`golemsp settings set --cpu-per-hour 3`

You can also combine multiple settings in one command as follows:

`golemsp settings set --cpu-per-hour 3 --cores 7` which will change your GLM per hour to "3" and adjust the numbers of shared CPU cores to "7".

**To change the default Ethereum address that was created for you during the initial setup process type:**

`golemsp settings set --account <address>`

and restart your node afterwards for it to update. To check if your address has been updated properly run `golemsp status`

#### Settings show

`golemsp settings show` - Show current settings.

example

```css
$ golemsp settings show
node name: "colorful-autumn"
Shared resources:
    cores:    7
    memory:    10.597366839647291 GiB
    disk:    138.55942993164064 GiB


Pricing:

        0 GLM for start
     0.02 GLM per hour
      0.1 GLM per cpu hour
```

### Status

`golemsp status` - Print out the status of your node.

When the node is not running you'll see:

```text
$ golemsp status
┌─────────────────────────────┐
│  Status                     │
│                             │
│  Service    is not running  │
│  Version    0.10.1          │
│  Commit     6ae8c21a        │
│  Date       2022-06-06      │
│  Build      223             │
│                             │
│  Node Name  cheetah         │
│  Subnet     public          │
│  VM         valid           │
└─────────────────────────────┘
```

When your node is already running `golemsp status` will show:

```text
$ golemsp status
┌──────────────────────────┬────────────────────────────────────────────────────┬─────────────────────────────┐
│  Status                  │  Wallet                                            │  Tasks                      │
│                          │  0xf98bb0842a7e744beedd291c98e7cd2c9b27f300        │                             │
│  Service    is running   │                                                    │  last 1h processed     0    │
│  Version    0.10.1       │  network               mainnet                     │  last 1h in progress   0    │
│  Commit     6ae8c21a     │  amount (total)        0 GLM                       │  total processed       0    │
│  Date       2022-06-06   │      (on-chain)        0 GLM                       │  (including failures)       │
│  Build      223          │      (polygon)         0 GLM                       │                             │
│                          │      (zksync)          0 GLM                       │                             │
│  Node Name  cheetah      │                                                    │                             │
│  Subnet     public       │  pending               0 GLM (0)                   │                             │
│  VM         valid        │  issued                0 GLM (0)                   │                             │
└──────────────────────────┴────────────────────────────────────────────────────┴─────────────────────────────┘
```

In the three columns, you can check the basic information regarding the status of your node

#### Status

- Whether your node is running
- Version of your node \(with commit, build date and build number\)
- Name of your node
- Subnet in which your node is currently running
- VM status

#### Wallet

- Account address
- Payment network: `mainnet` or `rinkeby`
- Amount of tokens that you have earned for successful computation
- On-chain amount of tokens that you have earned \(explorer [etherscan.io](https://etherscan.io/) or [rinkeby.etherscan.io](https://rinkeby.etherscan.io/)\)
- Zk-sync amount of tokens that you have earned \(explorer [zkscan.io](https://zkscan.io) or [rinkeby.zkscan.io](https://rinkeby.zkscan.io/)\)
- Pending payments that you should receive for computation
- Amount of tokens that is still unconfirmed and may not show on your account

#### Tasks

- Number of tasks that you were computing in last hour
- Number of tasks that were in progress during the last hour
- Total task that you were trying to compute - including those that were not computed

### Exit GLM tokens to Ethereum

While not specific to the provider CLI, at some point you may want to move your tokens. By default, mainnet tasks are paid on Layer 2. Assuming you have a local wallet, you can interact with the payment driver to exit your tokens from Layer 2 to Layer 1. This is done using the`yagna payment exit` command. With this command there are two main flags to keep in mind; `--network`and `--to-address`.

For `--network`you have two options, either `mainnet` or `rinkeby`. For `--to-address`you can specify a destination address other than the local wallet address.

**To exit your GLM to the same address on Ethereum mainnet type:**

`yagna payment exit --network=mainnet`

**To exit your GLM to a different address on Ethereum mainnet type:**

`yagna payment exit --to-address=<address> --network=mainnet`

**Note that if you decided to use an external wallet during your setup process, you can connect to ZkSync's wallet at** [**https://wallet.zksync.io/**](https://wallet.zksync.io/) **and exit that way. In the scenario that a different payment driver is being used, you will need to use the relevant available options to connect and access your tokens.**

## Advanced Settings

`ya-provider` allows to fine-tune the config created with `golemsp settings` using commands `config`, `preset`, `profile`, and `exe-unit`.

Additionally, it enables configuration of the rules, certificate keystore and of the domain whitelist, which are used to control what kind of outbound traffic is allowed out of the VM containers run by the requestors on your machine.

### Rules

Provider offers a mechanism that allows to control specific Rules for Outbound Network.

> **Warning**
> Remember, it is your responsibility as a provider to decide which entities you trust and the level of outbound access you want to enable for them.
> By default, the following rules and modes are set during installation:
>
> - Everyone: Whitelist mode (every requestor can access outbound until domain is whitelisted).
> - AuditedPayload: All mode (Golem root certificate is trusted).
> - Partner: All mode (another Golem root certificate is trusted).

#### Listing Rules

To list currently set rules, you can use the `ya-provider rule list` command. By default, it displays the rules in a table format:

```
$ ya-provider rule list
Outbound status: enabled
┌──────────────────┬─────────────┬───────────────┬───────────────┐
│  rule            │  mode       │  certificate  │  description  │
├──────────────────┼─────────────┼───────────────┼───────────────┤
│  Everyone        │  whitelist  │               │               │
│  AuditedPayload  │  all        │  55e451bd     │               │
│  Partner         │  all        │  80c84b27     │               │
└──────────────────┴─────────────┴───────────────┴───────────────┘
```

You can also retrieve the rules in JSON format by adding the `--json` flag:

```
$ ya-provider rule list --json
{
  "outbound": {
    "enabled": true,
    "everyone": "whitelist",
    "audited-payload": {
      "55e451bd1a2f43570a25052b863af1d527fe6fd4bfd1482fdb241596432477f20eb2b2f3801fb5c6cd785f1a03c43ccf71fd8cdf0a974d1296be2326b0824673": {
        "mode": "all",
        "description": ""
      }
    },
    "partner": {
      "80c84b2701126669966f46c1159cae89c58fb088e8bf94b318358fa4ca33ee56d8948511a397e5aba6aa5b88fff36f2541a91b133cde0fb816e8592b695c04c3": {
        "mode": "all",
        "description": ""
      }
    }
  }
}
```

#### Enabling and Disabling Outbound Traffic

You can enable or disable the entire outbound traffic regardless of other rules settings by using the following commands:

```
$ ya-provider rule set outbound disable
```

```
$ ya-provider rule set outbound enable
```

#### Setting Everyone Rule

To set the Everyone rule, use following command:

```
$ ya-provider rule set outbound everyone --mode <mode>
```

Replace `<mode>` with desired one (`all`, `whitelist`, or `none`).
Like so:

```
$ ya-provider rule set outbound everyone --mode none
```

#### Setting per-certificate Rules

`audited-payload` and `partner` rules, can be set only per-certificate.

To set these rules for a specific certificate by importing a certificate file directly, you can use the following command:

```
$ ya-provider rule set outbound <rule> import-cert <path/to/certificate/file> --mode <mode>
```

Replace `<path/to/certificate/file>` with the path to the certificate file you want to import, `<rule>` with desired per-certificate rule (`audited-payload` or `partner`) and `<mode>` with the desired mode (`all`, `whitelist`, or `none`).
For example:

```
$ ya-provider rule set outbound audited-payload import-cert ~/.local/share/ya-provider/cert_dir/foo_ca-chain.cert.pem --mode all
```

You can also specify the certificate ID instead of importing the certificate file. If the certificate is already present in the keystore, you can use the following command:

```
$ ya-provider rule set outbound <rule> cert-id <certificate-id> --mode <mode>
```

Replace `<certificate-id>` with the ID of the certificate you want to set the rule for, `<rule>` with desired per-certificate rule (`audited-payload` or `partner`) and `<mode>` with the desired mode (`all`, `whitelist`, or `none`).
For example:

```
$ ya-provider rule set outbound partner cert-id 80c84b27 --mode whitelist
```

### Keystore

The provider has an embedded certificate keystore which is used to keep certificates which then can be used by specific Rules.

By default it contains only Golem public certificates for `AuditedPayload` and `Partner` rules.

They allow to execute [example app](../requestor-tutorials/service-development/service-example-6-external-api-request.md) and apps from trusted by Golem creators (certificates allow to verify incoming _Demand_'s [Computational Payload Manifests](../requestor-tutorials/vm-runtime/computation-payload-manifest.md)).y default it contains only Golem public certificate which allows to execute [example app](../requestor-tutorials/service-development/service-example-6-external-api-request.md) and apps from trusted by Golem creators (certificates allow to verify incoming _Demand_'s [Computational Payload Manifests](../requestor-tutorials/vm-runtime/computation-payload-manifest.md)).

Run `ya-provider keystore --help` to see possible subcommands

### Domain whitelist

The [Computational Payload Manifests](../requestor-tutorials/vm-runtime/computation-payload-manifest.md) embedded in the Demands can specify a list of URLs which may get called by the services running on a Provider. If the manifest declares requests to URLs in domains that are not whitelisted, it must come with a [signature and app author's public certificate](../requestor-tutorials/vm-runtime/computation-payload-manifest.md). By default, the domains `whitelist` consists of a curated set of public websites and APIs like github, dockerhub or public Ethereum nodes.

Run `ya-provider whitelist --help` to see possible subcommands
