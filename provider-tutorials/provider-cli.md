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
golemsp 0.12.2 (8efd8657 2023-06-06 build #296)
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
golemsp-settings 0.3.0
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
golemsp-settings-set 0.3.0
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
        --payment-network <network>         Payment network [env: YA_PAYMENT_NETWORK_GROUP=]  [default: mainnet]
                                            [possible values: mainnet, testnet]

```

In order to change a particular setting (for eg. price settings) type:

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
node name: "zima"
Shared resources:
	cores:	7
	memory:	10.604358091950417 GiB
	disk:	59.39304809570313 GiB


Pricing for preset "vm":

	0.025000000000000001 GLM per cpu hour
	0.005000000000000000 GLM per hour
	0.000000000000000000 GLM for start


Pricing for preset "wasmtime":

	0.025000000000000001 GLM per cpu hour
	0.005000000000000000 GLM per hour
	0.000000000000000000 GLM for start

```

### Status

`golemsp status` - Print out the status of your node.

When the node is not running you'll see:

```
$ golemsp status
┌─────────────────────────────┐
│  Status                     │
│                             │
│  Service    is not running  │
│  Version    0.12.1          │
│  Commit     5671cd3f        │
│  Date       2023-05-23      │
│  Build      293             │
│                             │
│  Node Name  zima            │
│  Subnet     public          │
│  VM         valid           │
└─────────────────────────────┘

```

When your node is already running `golemsp status` will show:

```
$ golemsp status
┌─────────────────────────┬──────────────────────────────────────────────┬─────────────────────────────┐
│  Status                 │  Wallet                                      │  Tasks                      │
│                         │  0x2a14f8ae0272bd4c38ed1b40c66e88ed719dab69  │                             │
│  Service    is running  │                                              │  last 1h processed     0    │
│  Version    0.12.2      │  network               mainnet               │  last 1h in progress   0    │
│  Commit     5671cd3f    │  amount (total)        0 GLM                 │  total processed       509  │
│  Date       2023-06-06  │      (on-chain)        0 GLM                 │  (including failures)       │
│  Build      296         │      (polygon)         0 GLM                 │                             │
│                         │      (zksync)          0 GLM                 │                             │
│  Node Name  lato        │                                              │                             │
│  Subnet     public      │  pending               0 GLM (0)             │                             │
│  VM         valid       │  issued                0 GLM (0)             │                             │
└─────────────────────────┴──────────────────────────────────────────────┴─────────────────────────────┘

```

In the three columns, you can check the basic information regarding the status of your node

#### Status

- Whether your node is running
- Version of your node (with commit, build date and build number)
- Name of your node
- Subnet in which your node is currently running
- VM status

#### Wallet

- Account address
- Payment network: `mainnet` or `rinkeby`
- Amount of tokens that you have earned for successful computation
- On-chain amount of tokens that you have earned (explorer [etherscan.io](https://etherscan.io/) or [rinkeby.etherscan.io](https://rinkeby.etherscan.io/))
- Zk-sync amount of tokens that you have earned (explorer [zkscan.io](https://zkscan.io) or [rinkeby.zkscan.io](https://rinkeby.zkscan.io/))
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

## Outbound

`ya-provider` offers an outbound feature that allows to control the outbound traffic from the VM containers running on provider machine. This feature defines rules and modes for outbound access, ensuring the security and integrity for provider.

### Rules and Modes Overview

The outbound feature provides three rules that can operate in three different modes.

Modes:

1. `all`: all domains listed in the manifest can be accessed for outbound traffic.
2. `whitelist`: only whitelisted domains can be accessed for outbound traffic.
3. `none`: no outbound traffic is allowed.

Rules:

1. `Everyone`: This rule defines the default outbound access for all requestors.
   Any requestor can match this rule- nothing additional is needed.
2. `AuditedPayload`: This rule is set per certificate and controls outbound access for manifests which are audited and signed by a trusted party.
   Trust is gained when provider sets AuditedPayload rule for root certificate of auditing organisation.
   To match this rule, requestor should get his manifest audited and signed by organisation which is trusted by provider.
3. `Partner`: This rule is set per certificate and allows outbound access for any manifests, as long as requestor is a partner to trusted organisation.
   Trust is gained when provider sets Partner rule for root certificate of trusted organisation.
   To match this rule, requestor should get his node descriptor signed by partner to trusted organisation.

These rules and modes are designed to protect the provider against malicious use of outbound traffic. It gives you control over which entities are trusted and what level of outbound access they have. By default, the following rules and modes are set during installation:

- Everyone: Whitelist mode (every requestor can access outbound until domain is whitelisted).
- AuditedPayload: All mode (Golem root certificate is trusted).
- Partner: All mode (another Golem root certificate is trusted).

The purpose of these rules and modes is to maintain the security and integrity of the outbound traffic in the Golem network. You can customize and modify these rules based on your trust in specific certificates and entities.

> **_WARNING_** Remember, it is your responsibility as a provider to decide which entities you trust and the level of outbound access you want to enable for them.

### Outbound CLI

#### Listing Outbound Rules

To list currently set outbound rules, you can use the `ya-provider rule list` command. By default, it displays the rules in a table format:

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

#### Modifying Outbound Rules

##### Modifying the Everyone Rule

To set the Everyone rule:

```
$ ya-provider rule set outbound everyone --mode <mode>
```

Replace `<mode>` with desired one (`all`, `whitelist`, or `none`).

Like so:

```
$ ya-provider rule set outbound everyone --mode none
```

##### Modifying the AuditedPayload Rule

To set the AuditedPayload rule for a specific certificate by importing a certificate file, you can use the following command:

```
$ ya-provider rule set outbound audited-payload import-cert <path/to/certificate/file> --mode <mode>
```

Replace `<path/to/certificate/file>` with the path to the certificate file you want to import, and `<mode>` with the desired mode (`all`, `whitelist`, or `none`).

For example:

```
$ ya-provider rule set outbound audited-payload import-cert ~/.local/share/ya-provider/cert_dir/foo_ca-chain.cert.pem --mode all
```

You can also specify the certificate ID instead of importing the certificate file. If the certificate is already present in the keystore, you can use the following command:

```
$ ya-provider rule set outbound audited-payload cert-id <certificate-id> --mode <mode>
```

Replace `<certificate-id>` with the ID of the certificate you want to set the rule for, and `<mode>` with the desired mode (`all`, `whitelist`, or `none`).

For example:

```
$ ya-provider rule set outbound audited-payload cert-id 80c84b27 --mode whitelist
```

##### Modifying the Partner Rule

To set the Partner rule for a specific certificate, you can use the following command:

```
$ ya-provider rule set outbound partner cert-id <certificate-id> --mode <mode>
```

Replace `<certificate-id>` with the ID of the certificate you want to set the rule for, and `<mode>` with the desired mode (`all`, `whitelist`, or `none`).

For example:

```
$ ya-provider rule set outbound partner cert-id 80c84b27 --mode all
```

## Advanced Settings

`ya-provider` allows to fine-tune the config created with `golemsp settings` using commands `config`, `preset`, `profile`, and `exe-unit`.

Additionally, it enables configuration of the certificate keystore and of the domain whitelist, which are used to control what kind of outbound traffic is allowed out of the VM containers run by the requestors on your machine.

### Keystore

The provider has an embedded certificate keystore which is used to validate any additional permissions for the payload launched by the requestors.

By default it contains only Golem public certificate which allows to execute [example app](../requestor-tutorials/service-development/service-example-6-external-api-request.md) and apps from trusted by Golem creators (certificates allow to verify incoming _Demand_'s [Computational Payload Manifests](../requestor-tutorials/vm-runtime/computation-payload-manifest.md)).

Run `ya-provider keystore --help` to see possible subcommands

### Domain whitelist

The [Computational Payload Manifests](../requestor-tutorials/vm-runtime/computation-payload-manifest.md) embedded in the Demands can specify a list of URLs which may get called by the services running on a Provider. If the manifest declares requests to URLs in domains that are not whitelisted, it must come with a [signature and app author's public certificate](../requestor-tutorials/vm-runtime/computation-payload-manifest.md). By default, the domains `whitelist` consists of a curated set of public websites and APIs like github, dockerhub or public Ethereum nodes.

Run `ya-provider whitelist --help` to see possible subcommands
