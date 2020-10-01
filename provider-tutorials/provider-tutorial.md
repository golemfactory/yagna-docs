---
description: >-
  This tutorial shows how to run the new Golem Provider and play around with its
  limited functionalities.
---

# Becoming a provider

### Prerequisites

#### Platforms

This is our very first Alpha reveal. Therefore, temporarily, Golem only supports a limited list of platforms. These are those:

* OS X 10.14+
* Ubuntu 18.04 or 20.04

{% hint style="info" %}
For this release we have prepared a dedicated and controlled subnetwork using Ethereums Rinkeby Testnet for payments. If you would like to earn real GNT's head over to our [Clay Golem Beta implementation](https://golem.network/download/clay-beta/). This release also features [the basic CLI](https://golem-network.gitbook.io/golem-sdk-develop/reference/provider-cli) with which you may interact with your node.
{% endhint %}

## Installation

#### Purge directories

If you have previously used Golem Alpha on your machine run the command below that will purge its working directories since our newest version is incompatible with the old database structure:

```text
sudo dpkg -r yagna
```

#### Run the installation command

Open your terminal and type:

```text
curl -sSf https://join.golem.network/as-provider | bash -
```

#### Initial setup

After installing all required components you will be asked to set up your node

`node name:` - type the name of your new node and press enter

`subnet: community` - **It is important that you use "community" subnet for this release!**

`price NGNT per hour:` - type the value with witch you wish to start earning as a provider

{% hint style="success" %}
And that is it! You will see that default preset was created based on your initial node setup. You will be able to change some of this settings later on with CLI
{% endhint %}

## Running the provider

To run Golem type in the terminal:

```text
golem run
```

{% hint style="success" %}
Your provider node is up and running!
{% endhint %}

### Complete configuration guide

The complete configuration guide, please check following:

{% page-ref page="../reference/provider-cli.md" %}

## Next steps

