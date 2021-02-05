---
description: Golem Sneak Peek Provider Command Line Interface
---

# Provider CLI reference

{% hint style="info" %}
Keep in mind that that is a really basic release, and future updates will give you much more options to play with.
{% endhint %}

## CLI commands

Run `golemsp help` without arguments to see top-level usage information:

```text
golemsp 0.1.0-49c52869
User friedly CLI for running provider

USAGE:
    golemsp <SUBCOMMAND>

FLAGS:
    -h, --help       
            Prints help information

    -V, --version    
            Prints version information


SUBCOMMANDS:
    run         Run the golem provider
    stop        Stop the golem provider
    settings    Manage settings
    status      Show provider status
    help        Prints this message or the help of the given subcommand(s)
```

### Run

`golemsp run` - Start the Golem Sneak Peek provider.

### Settings

```text
golemsp-settings 0.1.0
Manage settings

This can be used regardless of whether golem is running or not.

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

`golemsp settings set` - Change settings.

In order to change a particular setting \(for eg. price settings\) type:

`golemsp settings set --cpu-per-hour 3`

You can also combine multiple settings in one command as follows:

`golemsp settings set --cpu-per-hour 3 --cores 7` which will change your tGLM per hour to "3" and adjust the numbers of shared cpu cores to "7".

**To change the default Ethereum address that was created for you during the initial setup process type:**

`golemsp settings set --address <address>`

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

        0 tGLM for start
        1 tGLM per hour
        5 tGLM per cpu hour
```

### Status

`golemsp status` - Print out the status of your node.

Example output:

```text
┌──────────────────────────────────────────────────────────────┐
│  Status                                                      │
│                                                              │
│  Service    is running                                       │
│  Version    0.5.0                                            │
│                                                              │
│  Node Name  outstanding-chalk                                │
│  Subnet     community.3                                      │
│  VM         valid                                            │
├──────────────────────────────────────────────────────────────┤
│  Wallet                                                      │
│                                                              │
│  address         0xe4781cd3af959417f560372544f77aec33124b5f  │
│  amount (total)  0 GLM                                       │
│      (on-chain)  0 GLM                                       │
│       (zk-sync)  0 GLM                                       │
│                                                              │
│  pending         0 GLM (0)                                   │
│  issued          0 GLM (0)                                   │
├──────────────────────────────────────────────────────────────┤
│  Tasks                                                       │
│                                                              │
│  last 1h processed    0                                      │
│  last 1h in progress  0                                      │
│  total processed      0                                      │
└──────────────────────────────────────────────────────────────┘
```

In the three columns, you can check the basic information regarding the status of your node

#### Status

* Whether your node is running
* Version of your node
* Name of your node
* Subnet in which your node is currently running
* VM status

#### Wallet

* Account address
* Amount of tokens that you have earned for successful computation
* On-chain amount of tokens that you have earned \(explorer [https://rinkeby.etherscan.io](https://rinkeby.etherscan.io/)\)
* Zk-sync amount of tokens that you have earned \(explorer [https://rinkeby.zkscan.io/](https://rinkeby.zkscan.io/)\)
* Pending payments that you should receive for computation
* Amount of tokens that is still unconfirmed and may not show on your account 

#### Tasks

* Number of tasks that you were computing in last hour
* Number of tasks that were in progress during the last hour
* Total task that you were trying to compute - including those that were not computed

