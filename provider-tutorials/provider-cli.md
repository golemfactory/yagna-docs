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
golemsp 0.10.0 (220c6399 2022-04-04 build #215)
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
│  Version    0.10.0          │
│  Commit     220c6399        │
│  Date       2022-04-04      │
│  Build      215             │
│                             │
│  Node Name  strange-spring  │
│  Subnet     public-beta     │
│  VM         valid           │
└─────────────────────────────┘
```

When your node is already running `golemsp status` will show:

```text
$ golemsp status
┌─────────────────────────────────────────┬────────────────────────────────────────────────────┬─────────────────────────────┐
│  Status                                 │  Wallet                                            │  Tasks                      │
│                                         │  0xc8e9d25c61706b4bdbd6029de9b40bfa45f77fba        │                             │
│  Service    is running                  │                                                    │  last 1h processed     0    │
│  Version    0.10.0                      │  network               mainnet                     │  last 1h in progress   0    │
│  Commit     220c6399                    │  amount (total)        0 GLM                       │  total processed       0    │
│  Date       2022-04-04                  │      (on-chain)        0 GLM                       │  (including failures)       │
│  Build      215                         │      (polygon)         0 GLM                       │                             │
│                                         │      (zksync)          0 GLM                       │                             │
│  Node Name  strange-spring              │                                                    │                             │
│  Subnet     public-beta                 │  pending               0 GLM (0)                   │                             │
│  VM         valid                       │  issued                0 GLM (0)                   │                             │
└─────────────────────────────────────────┴────────────────────────────────────────────────────┴─────────────────────────────┘
```

In the three columns, you can check the basic information regarding the status of your node

#### Status

* Whether your node is running
* Version of your node \(with commit, build date and build number\)
* Name of your node
* Subnet in which your node is currently running
* VM status

#### Wallet

* Account address
* Payment network: `mainnet` or `rinkeby`
* Amount of tokens that you have earned for successful computation
* On-chain amount of tokens that you have earned \(explorer [etherscan.io](https://etherscan.io/) or [rinkeby.etherscan.io](https://rinkeby.etherscan.io/)\)
* Zk-sync amount of tokens that you have earned \(explorer [zkscan.io](https://zkscan.io) or [rinkeby.zkscan.io](https://rinkeby.zkscan.io/)\)
* Pending payments that you should receive for computation
* Amount of tokens that is still unconfirmed and may not show on your account 

#### Tasks

* Number of tasks that you were computing in last hour
* Number of tasks that were in progress during the last hour
* Total task that you were trying to compute - including those that were not computed

### Exit GLM tokens to Ethereum

While not specific to the provider CLI, at some point you may want to move your tokens. By default, mainnet tasks are paid on Layer 2. Assuming you have a local wallet, you can interact with the payment driver to exit your tokens from Layer 2 to Layer 1. This is done using the`yagna payment exit` command. With this command there are two main flags to keep in mind; `--network`and `--to-address`. 

For `--network`you have two options, either `mainnet` or `rinkeby`. For `--to-address`you can specify a destination address other than the local wallet address.

**To exit your GLM to the same address on Ethereum mainnet type:**

`yagna payment exit --network=mainnet`

**To exit your GLM to a different address on Ethereum mainnet type:**

`yagna payment exit --to-address=<address> --network=mainnet`

**Note that if you decided to use an external wallet during your setup process, you can connect to ZkSync's wallet at** [**https://wallet.zksync.io/**](https://wallet.zksync.io/) **and exit that way. In the scenario that a different payment driver is being used, you will need to use the relevant available options to connect and access your tokens.**

