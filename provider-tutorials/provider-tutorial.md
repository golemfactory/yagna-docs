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

{% hint style="warning" %}
* For the time being all Linux systems with Intel processors should work properly. We are in the process of fixing issues with AMD
* To run the Golem Sneak Peek you should own physical machine as you may encounter issues when running it on virtual machine
{% endhint %}

{% hint style="info" %}
For this release we have prepared a dedicated and controlled subnetwork using Ethereum Rinkeby Testnet for payments. **This means that the tokens received for the rental of your computing power will not hold any value outside of the network**. This release also features [the basic CLI](https://golem-network.gitbook.io/golem-sdk-develop/reference/provider-cli) with which you may interact with your node.
{% endhint %}

{% hint style="info" %}
If you would like to earn real GNTs head over to our [Clay Golem Beta implementation](https://golem.network/download/clay-beta/).
{% endhint %}

## Installation

#### Purge directories

If you have previously used **Golem Alpha one** on your machine run the command below which will purge its working directories since our newest version is incompatible with the old database structure:

```text
rm -rf $HOME/.local/share/yagna
rm -rf $HOME/.local/share/ya-provider
```

#### Run the installation command

Open your terminal and type:

```text
curl -sSf https://join.golem.network/as-provider | bash -
```

You might be asked to modify your PATH afterwards: `PATH=$HOME/.local/bin:$PATH`

#### Initial setup

After installing all required components you will be asked to set up your node

`node name:` - Type in the name of your new node and press Enter

`subnet: community` - **It is important that you use "community" subnet for this release as only there we will be sending tasks for computation**

`price NGNT per hour:` - Type in the value of renting your computer power as a provider. You can use default price \(5 NGNT per hour\) by leaving this field empty. **This command shows up only when running GolemSP for the first time**

{% hint style="success" %}
Congrats, your initial setup has been completed! You will see that default preset was created based on your initial node setup. If you wish, you can change this settings later on with CLI.
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

To check your node's status and see if it is actually computing tasks from the network, open a new terminal window and type:

```text
golemsp status
```

As an output you will get the information about your node's current state as shown below: 

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
If in the \(far to the right\) **Tasks** column you see either tasks in progress or processed then you have successfully computed a task! If not, give it some time as there is still limited number of tasks in the test network - and then run the command again. 
{% endhint %}

#### Known issues

* Type `golemsp status` in your terminal window and check the status of your VM

**When there is other status than `valid`** 

a\) If: `the user has no access to /dev/kvm` run 

```text
curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh
```

and afterward log out, next log in into your OS and rerun `golemsp run`

b\) If: `running inside Docker without access to /dev/kvm` run

```text
docker run --privileged
```

c\) If: `unsupported virtualization type: XEN` We do not support **xen hypervisor**

* In any other case with the virtualisation we recommend:

`sudo apt install cpu-checker && sudo kvm-ok` command and follow the steps as given in the terminal interface. 

## Provider CLI

To check additional commands available in CLI check the reference page:

{% page-ref page="../reference/provider-cli.md" %}

## Next steps

