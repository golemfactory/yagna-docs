---
description: >-
  This tutorial shows how to run the new Golem Provider Sneak Peek release and
  play around with its limited functionalities.
---

# Becoming a provider

### Prerequisites

#### Platforms

This is our very first Alpha Provider Sneak Peek reveal. Therefore, temporarily, Golem only supports:

* Ubuntu 18.04 and 20.04

{% hint style="info" %}
For this release we have prepared a dedicated and controlled subnetwork using Ethereums Rinkeby Testnet for payments. **This means that all the tokens for your computing power will not have any value**. If you would like to earn real GNT's head over to our [Clay Golem Beta implementation](https://golem.network/download/clay-beta/). This release also features [the basic CLI](https://golem-network.gitbook.io/golem-sdk-develop/reference/provider-cli) with which you may interact with your node.
{% endhint %}

## Installation

#### Purge directories

If you have previously used Golem Alpha.1 on your machine run the command below that will purge its working directories since our newest version is incompatible with the old database structure:

```text
rm -rf $HOME/.local/share/yagna
```

#### Run the installation command

Open your terminal and type:

```text
curl -sSf https://join.golem.network/as-provider | bash -
```

You might be asked to modify your PATH afterwards: `PATH=$HOME/.local/bin:$PATH`

#### Initial setup

After installing all required components you will be asked to set up your node

`node name:` - Type the name of your new node and press enter

`subnet: community` - **It is important that you use "community" subnet for this release!**

`price NGNT per hour:` - Type the value with witch you wish to start earning as a provider. You can leave it empty with default value. **This command shows up only with first run of GolemSP**

{% hint style="success" %}
And that is it! You will see that default preset was created based on your initial node setup. You will be able to change this settings later on with CLI
{% endhint %}

## Running the provider

To run Golem Sneak Peek type in the terminal:

```text
golemsp run
```

{% hint style="success" %}
Your provider node is up and running!
{% endhint %}

### Checking node status

Now the question is if your node is actually computing tasks from the network. To check its status open a new terminal window and type:

```text
golemsp status
```

As an output you will get current information about your node state as seen below: 

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

{% hint style="info" %}
If in the \(far to the right\) **Tasks** section of the table you will see either tasks in progress or processed then you have successfully computed a task! If not, give it some time as there is still not many tasks in the test network - and then run the command again. 
{% endhint %}

#### Known issues

In case there is other status than `valid` in your `VM`:

a\). For: `the user has no access to /dev/kvm` run 

```text
curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh
```

and afterward log out and in again into your OS. 

b\). For: `running inside Docker without access to /dev/kvm` run

```text
docker run --privliged
```

c\). For: `unsupported virtualization type: XEN` We do not support **xen hypervisor**

In any other case with the virtualisation we recommend:

`sudo apt install cpu-checker && sudo kvm-ok` command and follow the steps from the terminal interface. 

## Provider CLI

To check additional commands available in CLI check the reference page:

{% page-ref page="../reference/provider-cli.md" %}

## Next steps

