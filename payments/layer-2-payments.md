---
description: Better solution for computation cost reimbursements
---

# Layer 2 payments

## The problem

Ever since the launch of the previous incarnation of Golem on mainnet, we have been facing one very serious problem which should be obvious to anyone who ever played around with implementing an application that needs to execute payments of very small amounts on the Ethereum blockchain - namely, the transaction costs.

When payments are performed directly on Ethereum, each payment must be executed as a transaction on the main chain which incurs a fee required for the transaction to be mined and included in the blockchain. The problem becomes much more pronounced whenever the average gas price or the price of the ETH token - which every Ethereum transaction fee is paid with - rises.

In the past, we have explored various solutions to this problem and actively implemented a few of them but until recently, none of them seemed useful and mature enough to resolve the problem completely.

## Enter layer 2

Last year's [migration of our token to a new, ERC-20-compliant contract](https://glm.golem.network/) enabled us to not only leverage decentralized exchanges and other DeFi platforms on Ethereum but most importantly, made it possible to utilize a variety of Layer 2 solutions popping up within the Ethereum ecosystem.

The common feature of all the platforms gathered under the "Layer 2" umbrella is that they move most of the transactions to their own side chains while maintaining a varying degree of synchronization with the base Ethereum chain. 

Because what makes Ethereum mainnet so expensive is mostly its globally-distributed, proof-of-work-based consensus mechanism, layer 2 solutions implement their own ways to ensure integrity of their side chains. The net effect is that cost of a singular transaction is reduced, sometimes by several orders of magnitude. The usual tradeoff is some level of centralization which, arguably, reduces the trustless-ness and thus, to smaller or larger extent, also the security of users' funds.

### zkSync

ZkSync happened to be the first layer-2 platform that we started supporting in Golem. It is a layer-2 protocol that enables scaling of transactions both in terms of cost and throughput while preserving close-to-mainnet security thanks to the underlying zero-knowledge proofs that are used to validate the correctness of its state changes.

zkSync supports close-to-immediate transactions involving both ETH itself and potentially any ERC-20-compatible token. Additionally, the transactions fees can be paid in the token that's transferred, eliminating the need for the sender to be in posession of ETH.

Thanks to the underlying technology, namely zkRollup, the validators in zkSync are able to process thousands of transactions in a single block. The hash of such a block and a cryptographic proof that the block is a result of an application of a series of correct state transitions is published to Ethereum blockchain. Alongside it, the delta change resultant from execution of all the included transactions is also published to the blockchain and both the delta and the proof are validated by a smart contract.

The net effect is that, with smaller costs and higher transaction throughput, zkSync remains almost as secure as the Ethereum mainnet itself.

Unfortunately, zkSync also has two major drawbacks. The first one is that, while the transaction fees are indeed smaller, they're still uneconomically high for zkSync to serve as a viable platform for Golem, where the transactions happen often and the paid amounts tend to be relatively low. The second one is that - zkSync being a closed, single-purpose network - it currently has no potential to sustain DeFi and thus, tokens accumulated by users cannot be used otherwise than only after the specific user exits zkSync, which, because it requires committing a transaction to the Ethereum mainchain, is prohibitively expensive unless the user was able to collect a sizable amount. 

### Polygon

Formerly dubbed "Matic", Polygon is becoming a de-facto standard for a lot of decentralized apps in the Ethereum space. Technically, it could be argued that it's not really a "Layer 2" solution as it doesn't keep in sync with the Ethereum but rather maintains its own side chain, connected to the Ethereum main chain with a set of inter-chain bridges.

What makes Polygon attractive is that its chain is fully compatible with the Ethereum, making all the smart contracts, wallets and other applications currently working with Ethereum immediately usable on Polygon. One noticeable difference is that in place of the ETH token, the Polygon chain uses its own MATIC token to pay the transaction fees.

The consensus on Polygon's mainnet chain is maintained by a carefully selected and somewhat decentralized set of validator nodes who use a proof-of-stake mechanism, whereby the validators stake their MATIC tokens. Because of this set-up and because no active synchronization with the Ethereum is attempted, the costs of transactions are several orders of magnitude lower than on Ethereum.

A user wishing to enter and exit Polygon - that is transfer funds between Polygon and the Ethereum mainnet - needs to use a bridge - a special kind of contract that locks user's funds on one chain and transfers them a respective amount on the other chain. Because those bridges need to work on the Ethereum, they're pretty costly to interact with. 

The good news is that a user having funds on Polygon - e.g. someone who received tokens as a Golem provider - may not have an immediate need to exit from Polygon to mainnet as there are a lot of centralized and decentralized exchanges and other kinds of DeFi solutions already operating directly _on_ the Polygon chain.

Moreover, from the perspective of Golem requestors, Polygon is currently an indisputably superior solution because the ratio between the amounts paid for computing resources and the transaction fees is much more favorable than on the main chain or on zkSync. 

## Current support in Golem

The providers are ready to receive payments on any of the supported platforms - be it the Ethereum, Polygon or zkSync. Obviously, by default, they expect those payments to be made on the respective mainnet chains.

On the other hand, because we assume requestors will first start by testing the ground using their just-created apps on a testnet, the default payment platform for those nodes is ERC20/Rinkeby.

Please note that while we're still leaving zkSync enabled by default on Providers to enable a smooth transition after the launch of Polygon support in yagna, we'll be disabling that default in a close future. We also intend to give our current providers a sensible solution to make the funds they have accumulated so far, available on Polygon. 

When you run `yagna payment fund` on testnet, Golem initializes a new account from our custom faucet \(a service that transfers test tokens to an address that asks for it\) which provides it with test ETH and GLM tokens.

Of course, you also need to enable your accounts' sender mode, which is done using `yagna payment init --sender`. All this is covered in [our requestor introduction](../requestor-tutorials/flash-tutorial-of-requestor-development/).

If you're interested in running a requestor on the Ethereum mainnet, to be able to leverage the main pool of Golem providers, please refer to:

{% page-ref page="using-golem-on-mainnet/README.md" %}

## Further reading

* [Polygon intro](https://polygon.technology/technology/)
* [ZkSync intro](https://zksync.io/faq/intro.html)
