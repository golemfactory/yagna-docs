---
description: >-
  This tutorial shows how to run a Golem Provider node and play around with its
  functionalities.
---

# Becoming a provider

### Prerequisites

#### Platforms

For the provider end, we currently, officially support:

* Ubuntu 18.04 LTS and 20.04 LTS

but you are welcome to try out and run it on other Linux distributions. 

{% hint style="warning" %}
To run a Golem provider node we recommend a physical machine as you may encounter issues and limitations when running it on a virtual machine. Because we expect most apps to use vm-based payloads, we don't recommend running a provider on non-Linux platforms. 

It is possible to use macOS and Windows as provider hosts, but only with WASI execution environment.
{% endhint %}



{% hint style="info" %}
For this release we have enabled the providers to expect payments on the Ethereum mainnet by default. It means that by running a provider node and executing tasks, you'll be **earning real GLM tokens** - either as pure ERC-20 tokens or on zkSync.
{% endhint %}

## Installation

#### Purge directories

{% hint style="danger" %}
**BEFORE YOU PROCEED** - if you have ever run your Golem on mainnet and you have earned GLM tokens or funded your Golem account with ETH/GLM - **DO NOT purge** your data directories before you have backed-up your Golem wallet and confirmed that you can safely recover it.

For instructions on how to do it, consult our [guide on using Golem on Mainnet](../payments/using-golem-on-mainnet.md#backing-up-your-golem-wallet) and specifically its backup/recovery section.
{% endhint %}

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

You might be asked to modify your PATH afterwards for future terminal sessions:`echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc`

Update your active shell\(s\) with:  
`export PATH="$HOME/.local/bin:$PATH”`

#### Initial setup

After installing all required components you will be asked to set up your node. **If you leave them empty the default values presented in brackets will be applied.**

`Node name (default=generated_name):` - Type in the name of your new node and press Enter

`subnet (default=community.4):` - It is important that you use "community.4"

`Ethereum wallet address (default=internal wallet):`  - Paste your own Ethereum address to which you have private keys stored. If you leave this space empty an address will be created for you on your local system.

{% hint style="info" %}
This is especially important now that the providers are by default using **Ethereum mainnet** - this way, you can have your earned GLM tokens sent directly e.g. to your MetaMask or Ledger account and you can manage them from there without Golem ever needing to touch your wallet - do that especially if you don't plan on becoming a Requestor.
{% endhint %}

`price GLM per hour (default=0.1):` - Type in the value of renting your computer power as a provider. You can use default price \(0.1 GLM per hour\) by leaving this field empty. **This command shows up only when running GolemSP for the first time**

{% hint style="success" %}
Congrats, your initial setup has been completed! You will see that default preset was created based on your initial node setup. If you wish, you can change this settings later on with CLI.
{% endhint %}

## Running the provider

To run a Golem provider, type the following in the terminal:

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
│  Subnet     community.4                          │
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

{% hint style="info" %}
Under your address you can see both **on-chain** and **zk-sync** values listed. 

Although zk-sync is from now on the main payment operator in Golem you may receive on-chain transactions as well. To confirm the correctness of the listed values head over to [https://etherscan.io/](https://etherscan.io/) \(on-chain\) and [https://zkscan.io/](https://zkscan.io/) \(for zk-sync\).
{% endhint %}

{% hint style="info" %}
If in the **Offers/Tasks** column you see your active Offers count, and either tasks in progress or processed then you have successfully computed! If not, give it some time as there is still a limited number of tasks in the network - and then run the command again.
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

