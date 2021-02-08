---
description: >-
  This tutorial shows how to run the new Golem Provider Sneak Peek release and
  play around with its limited functionalities.
---

# Becoming a provider

### Prerequisites

#### Platforms

This is still an early Alpha Provider Sneak Peek reveal. Therefore, temporarily, Golem official support is for:

* Ubuntu 18.04 and 20.04 

but you are welcome to try out run it on other Linux distributions.

{% hint style="warning" %}
* To run Golem Sneak Peek you'll need a physical machine as you may encounter issues when running it on a virtual machine.
{% endhint %}

{% hint style="info" %}
For this release we have prepared a dedicated and controlled sub-network using Ethereum Rinkeby Testnet for payments. **This means that the tokens received for the rental of your computing power will not hold any value outside of the network**. This release also features [the basic CLI](https://golem-network.gitbook.io/golem-sdk-develop/reference/provider-cli) with which you may interact with your node.
{% endhint %}

{% hint style="info" %}
If you would like to earn real GNTs now, head over to our [Clay Golem Beta implementation](https://golem.network/download/clay-beta/).
{% endhint %}

## Installation

#### Purge directories

If you have previously launched **Golem Alpha** on your machine run the command below which will purge its working directories since our newest version is incompatible with the old database structure:

```text
rm -rf $HOME/.local/share/yagna
rm -rf $HOME/.local/share/ya-provider
```

#### Run the installation command

Open your terminal and type:

```text
curl -sSf https://join.golem.network/as-provider | bash -
```

You might be asked to modify your PATH afterwards For future terminal sessions:`echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc`

Update your active terminal\(s\) with:  
`export PATH="$HOME/.local/bin:$PATH"`

#### Initial setup

After installing all required components you will be asked to set up your node. **If you leave them empty the default values presented in brackets will be applied.**

`Node name (default=generated_name):` - Type in the name of your new node and press Enter

`subnet (default=community.3):` - It is important that you use "community.3"

`Ethereum wallet address (default=internal wallet):` - Paste your own Ethereum address to which you have private keys stored. If you leave this space empty an address will be created for you on your local system.

`price tGLM per hour (default=5):` - Type in the value of renting your computer power as a provider. You can use default price \(5 tGLM per hour\) by leaving this field empty. **This command shows up only when running GolemSP for the first time**

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

{% hint style="info" %}
Under your address you can see both **on-chain** and **zk-sync** values listed.

Although zk-sync is from now on the default payment driver in Golem you may receive on-chain transactions as well. To confirm correctness of the listed values head over to [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io/) \(on-chain\) and [https://rinkeby.zkscan.io/](https://rinkeby.zkscan.io/) \(for zk-sync\).
{% endhint %}

{% hint style="info" %}
If in the **Tasks** column you see either tasks in progress or processed then you have successfully computed a task! If not, give it some time as there is still limited number of tasks in the test network - and then run the command again.
{% endhint %}

#### Known issues

* Type `golemsp status` in your terminal window and check the status of your VM

**When there is other status than `valid`**

a\) If: `the user has no access to /dev/kvm` run

```text
curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh
```

Afterwards, log out and log in again into your OS and then, rerun `golemsp run`

b\) If: `running inside Docker without access to /dev/kvm` run

```text
docker run --privileged
```

c\) If: `unsupported virtualization type: XEN` We do not support **xen hypervisor**

* In any other case with the virtualisation we recommend:

`sudo apt install cpu-checker && sudo kvm-ok` command and follow the steps as given in the terminal interface.

## Provider CLI

To check out additional commands available in the CLI, have a look at the reference page:

{% page-ref page="../reference/provider-cli.md" %}

## Next steps

