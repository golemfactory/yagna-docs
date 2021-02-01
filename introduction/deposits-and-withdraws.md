---
description: How to move and ensure safety of your funds when operating on mainnet
---

# Using Golem on Mainnet

Okay, so we've seen Golem requestors hand out tasks to providers and saw them pay those providers for the successfully executed tasks. We've also seen how we could use layer 2 \(zkSync\) to speed up those payments and significantly cut the transactions fees.

Still, a few questions remain largely unanswered:

* how do you get funds to your requestor so you can use them to pay for the tasks?
* how do you get funds out of a Golem node if you don't need them there anymore?
* how to secure access to the funds in your Golem wallet if things go haywire?

## ERC-20 vs Layer2

The most important distinction in basically every piece of payment-related activity, both when you consider transactions between the network's nodes but also when talking about getting funds in and out of Golem is whether you're using the regular ERC-20 token directly on the Ethereum blockchain or whether you're using zkSync.

While direct, on-chain transactions using ERC-20-based tokens have long become the daily bread for the Ethereum mainnet and constitute a significant part of more than a million transactions passing through the chain each day, the recent spike in both the ETH's price and the average gas prices makes it almost completely useless as a means of exchange in Golem where the value paid will usually be orders of magnitude smaller than the fee for the payment itself.

Of course, if you're willing to accept that disproportion, you may continue to use our ERC-20 payment driver but for the majority of Golem node users, zkSync will be the main platform both when paying for tasks and receiving payments for their execution.

## Initialize your Golem wallet

\[ is this needed ? \]

## Sending funds to your account

#### zkSync

So far the only supported way to enable your requestor wallet to operate on zkSync is to reach out to us to get your address funded with some GLM tokens.

First, establish the address of your account with:

```text
yagna payment accounts
```

And take note of the address of your Golem node. With the address, reach out to us on our Discord at [https://chat.golem.network](https://chat.golem.network) where, after a short verification process, you'll be issued some GLM tokens directly to your zkSync wallet and your Golem node will be good to go!

The same instruction, already containing your mainnet adress can be obtained by running:

```text
yagna payment fund --network=mainnet --driver=zksync
```

#### ERC-20

On the other hand, if you'd like to use the regular ERC-20 transactions to pay the providers, you'll need to provide your address with some actual GLM tokens, plus some ETH to pay for all the gas fees.

The same as in case of zkSync above, you'll need to establish the address of your node's account using:

```text
yagna payment accounts
```

And then use you regular wallet to send some GLM and ETH tokens there.

Again, you'll get the same instruction plus your mainnet address if you just run:

```text
yagna payment fund --network=mainnet --driver=erc20
```

## Getting your funds out of the Golem node

#### zkSync

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

#### ERC-20

\[ content needed \]

### Backing up your Golem wallet

As you're probably aware, in the Ethereum universe, your funds are only as secure as the private key for the account that holds them. Because of that, to ensure that you don't lose access to your GLM/ETH tokens stored on your Golem account, it's crucial for you to be able to back-up your Golem wallet and store the key in a safe storage, separate from the node itself.

To create a backup of your Golem wallet, export it with:

```text
yagna id export --file-path=./key.json
```

The resultant `key.json` file in the directory you ran the command from will contain the private key for your Golem wallet.

{% hint style="danger" %}
Ensure you store that key file in a safe place. In case your Golem wallet gets corrupted or lost, if you don't have the backup, your funds will be lost forever.
{% endhint %}

