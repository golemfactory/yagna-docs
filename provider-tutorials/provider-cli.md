---
description: Golem Provider Command Line Interface
---

# Provider CLI reference

{% hint style="info" %}
Keep in mind that that is a really basic release, and future updates will give you much more options to play with.
{% endhint %}

## CLI commands

Run `golemsp help` without arguments to see top-level usage information:

```text
golemsp 0.6.0 (ed55e851 2021-02-15 build #113)
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

```text
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

`golemsp settings set --help` - to see how to change settings.

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

```text
node name: "node_name"
shared resources:
    cores:     7
    memory:    10.9375 GiB
    disk:      250.2247528076172 GiB


Pricing:

        0 NGNT for start
        1 NGNT per hour
        5 NGNT per cpu hour
```

### Status

`golemsp status` - Print out the status of your node.

Example output:

```text
┌──────────────────────────────────────────────────┐
│  Status                                          │
│                                                  │
│  Service    is running                           │
│  Version    0.6.0                                │
│  Commit     ed55e851                             │
│  Date       2021-02-15                           │
│  Build      113                                  │
│                                                  │
│  Node Name  tenuous-condition                    │
│  Subnet     public-beta                          │
│  VM         valid                                │
├──────────────────────────────────────────────────┤
│  Wallet                                          │
│  0x979db95461652299c34e15df09441b8dfc4edf7a      │
│                                                  │
│  network               mainnet                   │
│  amount (total)        5.261287428341905586 GLM  │
│      (on-chain)        1.618008610566005586 GLM  │
│       (zk-sync)        3.6432788177759 GLM       │
│                                                  │
│  pending               0 GLM (0)                 │
│  issued                0 GLM (0)                 │
├──────────────────────────────────────────────────┤
│  Offers                                          │
│                                                  │
│  Subscribed           2                          │
│                                                  │
│  Tasks                                           │
│                                                  │
│  last 1h processed    1                          │
│  last 1h in progress  0                          │
│  total processed      1                          │
└──────────────────────────────────────────────────┘
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

#### Offers

* Number of currently subscribed \(ie. published\) Offers by your node.  

#### Tasks

* Number of tasks that you were computing in last hour
* Number of tasks that were in progress during the last hour
* Total task that you were trying to compute - including those that were not computed

