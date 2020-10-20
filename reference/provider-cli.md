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

`golemsp settings set --cpu-per-hour 3 --cores 7` which will change your NGNT per hour to "3" and adjust the numbers of shared cpu cores to "7".

#### Settings show

`golemsp settings show` - Show current settings.

example

```text
node name: "node_name"
shared resources:
    cores:    7
    memory:    10.9375 GiB
    disk:    250.2247528076172 GiB


Pricing:

        0 NGNT for start
        1 NGNT per hour
        5 NGNT per cpu hour
```

### Status

`golemsp status` - Print out the status of your node.

Example output:

```text
┌─────────────────────────────┬───────────────────────────────────────────────────────────┬───────────────────────────┐
│  Status                     │  Wallet                                                   │  Tasks                    │
│                             │                                                           │                           │
│  Service    is running      │  address      0x8ed221a17e63b129c1a2aa1fc2cb331cdff1a21d  │  last 1h processed    0   │
│                             │  amount       0 NGNT                                      │  last 1h in progress  1   │
│  Node Name  node_name       │  pending      0 NGNT                                      │  total processed      0   │
│  Subnet     community       │  unconfirmed  0 NGNT                                      │                           │
|  VM         valid           |                                                           |                           | 
└─────────────────────────────┴───────────────────────────────────────────────────────────┴───────────────────────────┘
```

In the three columns, you can check the basic information regarding the status of your node

#### Status

* Whether your node is running
* Name of your node
* Subnet in which your node is currently running
* VM status

#### Wallet

* Account address
* Amount of tokens that you have earned for successful computation
* Pending payments that you should receive for computation
* Amount of tokens that is still unconfirmed and may not show on your account 

#### Tasks

* Number of tasks that you were computing in last hour
* Number of tasks that were in progress during the last hour
* Total task that you were trying to compute - including those that were not computed

