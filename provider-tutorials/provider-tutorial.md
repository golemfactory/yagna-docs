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

{% hint style="success" %}
We have enabled the providers to expect payments on the Ethereum mainnet by default. It means that by running a provider node and executing tasks, you are **earning real GLM tokens** - either on Ethereum mainnet or on Polygon.
{% endhint %}

## Installation

#### Run the installation command

Open your terminal and type:

```
curl -sSf https://join.golem.network/as-provider | bash -
```

You might be asked to modify your PATH afterwards for future terminal sessions:`echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc`

Update your active shell(s) with: `export PATH="$HOME/.local/bin:$PATH"`

#### Initial setup

After installing all required components you will be asked to set up your node. **If you leave them empty the default values presented in brackets will be applied.**

`Node name (default=generated-name):` - Type in the name of your new node and press Enter

`Ethereum wallet address (default=internal wallet):` - Paste your own Ethereum address to which you have private keys stored. If you leave this space empty, an address will be created for you on your local system.

{% hint style="info" %}
Your own Ethereum address could be, for example, any MetaMask or Ledger address that only you control so you can access your tokens from that address. If you choose to have a local wallet it's recommended to store a [backup](../payments/using-golem-on-mainnet/backing-up-your-golem-wallet.md) somewhere safe so you can retrieve the tokens. You are responsible for your address. If you lose access to the wallet, there will be no way to retrieve them without a backup.
{% endhint %}

`price GLM per hour (default=0.1):` - Type in the value of renting your computer power as a provider. You can use default price (0.1 GLM per hour) by leaving this field empty. **This command shows up only when running GolemSP for the first time**

{% hint style="success" %}
Congrats, your initial setup has been completed! You will see that default preset was created based on your initial node setup. If you wish, you can change this settings later on with CLI.
{% endhint %}

## Running the provider

### Mainnet

To run the Golem provider on the mainnet, type the following in the terminal:

```
golemsp run
```

### Testnet

To run the Golem provider on the testnet, type the following in the terminal:

```
golemsp run --payment-network testnet --subnet devnet-beta
```

{% hint style="success" %}
Your provider node is up and running!
{% endhint %}

{% hint style="info" %}
Please keep in mind that golemsp run will remember last time used parameters,

After you do your tests you need to change back into public network :
{% endhint %}

```
golemsp run --subnet public-beta --payment-network mainnet
```

### Checking node status

To check your node's status and see if it is actually computing tasks from the network, open a new terminal window and type:

```
golemsp status
```

As an output you will get the information about your node's current state as shown below:

```
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

{% hint style="info" %}
Under your address you can see both **on-chain** and **zk-sync** values listed.

Although zk-sync is from now on the main payment operator in Golem you may receive on-chain transactions as well. To confirm the correctness of the listed values head over to [https://etherscan.io/](https://etherscan.io) (on-chain) and [https://zkscan.io/](https://zkscan.io) (for zk-sync).
{% endhint %}

{% hint style="info" %}
If in the **Offers/Tasks** column you see your active Offers count, and either tasks in progress or processed then you have successfully computed! If not, give it some time as there is still a limited number of tasks in the network - and then run the command again.
{% endhint %}

## Provider CLI

To check out additional commands available in the CLI, have a look at the reference page:

{% content-ref url="provider-cli.md" %}
[provider-cli.md](provider-cli.md)
{% endcontent-ref %}
