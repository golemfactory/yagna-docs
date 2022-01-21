---
description: your Golem wallet and yagna setup for Mainnet payments.
---


# Your Golem wallet

{% hint style="info" %}
All instructions in this section assume that you have your daemon launched on another terminal. In case you forgot the command to run the daemon, it's:

`yagna service run`

If you get any errors while running the other commands here, first always ensure that your daemon is still running correctly.
{% endhint %}

Golem's wallet is automatically initialized for you the first time you start your `yagna` daemon and thus, an address associated with it is also generated automatically.

Obviously, to have any kind of funds transferred to your Golem's wallet, you'll need its address. You may obtain it using the `id` command:

```text
yagna id show
```

The value described as `nodeId` in the output is the Ethereum address of your Golem node and it's also the address of its wallet. Note it down so you can use it to supply your node with funds.

## Sending funds to your account

### ERC-20 / Ethereum mainnet

To use be able to pay the providers and run tasks on the mainnet (be it Ethereum or Polygon), you'll first need to supply your address with some actual GLM tokens, plus some ETH/MATIC to pay for all the gas fees. Just use you regular wallet to send some GLM and ETH/MATIC tokens to the node's address.

You'll get the instructions plus your mainnet address if you run:

{% tabs %}
{% tab title="Polygon" %}
```bash
yagna payment fund --network=polygon --driver=erc20
```
{% endtab %}
{% tab title="Ethereum mainnet" %}
```bash
yagna payment fund --network=mainnet --driver=erc20
```
{% endtab %}
{% endtabs %}


## Enable the mainnet account

In the current version of requestor's set-up, the daemon is configured to use the Rinkeby testnet by default. Also, all accounts are initialized in the receiver mode by default so you need to enable them as a sender \(that's the reason we're adding the `--sender` flag below\).

In order to enable the daemon to use the mainnet, you'll need to instruct it so using a command appropriate to your desired mainnet payment platform.


{% tabs %}
{% tab title="Polygon" %}
```bash
yagna payment init --sender --network=polygon --driver=erc20
```
{% endtab %}
{% tab title="Ethereum mainnet" %}
```bash
yagna payment init --sender --network=mainnet --driver=erc20
```
{% endtab %}
{% endtabs %}


{% hint style="warning" %}
Again, unless you have good reasons not to, we recommend using Polygon for the lowest transaction fees.
{% endhint %}

{% hint style="danger" %}
The initialization must be performed after every restart of the `yagna` daemon.
{% endhint %}

## Checking the status of your accounts

Depending on whether you're mainly running a provider node or a requestor one, your default network \(blockchain\) may be different.

Because of that, when you run `yagna payment status` to verify the state of your payment account and the amount of GLM tokens you have in your disposal, you may need to add the specific `network` and `driver` parameters to point to the network/driver combination that you're interested in.

In the context of running Golem on mainnet, here are the commands for each of the supported mainnet platforms:


{% tabs %}
{% tab title="Polygon" %}
```bash
yagna payment status --sender --network=polygon --driver=erc20
```
{% endtab %}
{% tab title="zkSync" %}
```bash
yagna payment status --sender --network=mainnet --driver=zksync
```
{% endtab %}
{% tab title="Ethereum mainnet" %}
```bash
yagna payment status --sender --network=mainnet --driver=erc20
```
{% endtab %}
{% endtabs %}


## Getting your funds out of the Golem node

### zkSync

If you'd like to convert your GLM tokens on zkSync back to regular ERC-20 GLM tokens on the Ethereum blockchain, you need to exit the zkSync Layer2.

There are two ways you may perform this operation. In the first case, you may exit from zkSync to the same address. As a result, your GLM tokens will once more become regular ERC-20 tokens and will stay within the same wallet they were in. To do that, just issue the following command:

```text
yagna payment exit --network=mainnet
```

The alternative option is to provide an address to which the exit should be performed. That way, instead of sending the tokens to the address the request was signed by, zkSync will send them to the address you have provided. This is especially useful if you no longer need to use the GLM tokens within the Golem network and would rather have them back on your regular cryptocurrency wallet that may be completely independent of Golem. The command you need is:

```text
yagna payment exit --to-address=YOUR-ETHEREUM-ADDRESS --network=mainnet
```

{% hint style="danger" %}
Be careful though, as Golem does not perform any validation of the supplied address.
{% endhint %}

### ERC-20

It is easiest to access your ERC-20 tokens by using the functionality described below to export your wallet \(in Ethereum wallet v3 format\) and then import it into MetaMask. Once you import your private key to MetaMask you'll be able to withdraw your ERC-20 tokens.

