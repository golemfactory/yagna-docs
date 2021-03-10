---
description: Better solution for computation cost reimbursements
---

# Layer 2 payments on zkSync

## The problem

Ever since the launch of the previous incarnation of Golem on mainnet, we have been facing one very serious problem which is obvious for anyone who tried implementing an application that tries to execute payments of very small amounts on Ethereum blockchain - namely, the transaction costs.

When payments are performed directly on Ethereum, each payment must be executed as a transaction and that means that a fee needs to be paid in order for the transaction to be mined and included in the blockchain. The problem becomes much more serious whenever the average gas price or the price of the ETH token - with which every Ethereum transaction fee is paid - rises.

In that previous version - dubbed Brass and later Clay - we implemented batch payments. It added a lot of complexity to achieve a very dubious cost decrease. Apart from that we briefly flirted with various ideas on decreasing the costs like probabilistic payments, payment channels, plasma, and so on and so on, and until recently, none of them seemed to be ideal and mature enough to use right away.

## The solution - zkSync

It all changes with the new Golem. That's because the new Golem uses our new, upgraded, ERC-20-compliant token, which, by the way, all current GNT holders already have an ability to migrate to, thanks to the [recently-enabled migration](https://glm.golem.network/) process.

While the new token's ERC-20 compliance enables integration with a whole lot of other contracts and DeFi platforms present in the Ethereum ecosystem, it also, specifically, enables integration with zkSync. And zkSync happens to be our latest answer to the aforementioned problem of increasing transactions costs in the Ethereum mainnet.

### What is this zkSync thing then?

zkSync is a new layer-2 protocol that enables scaling of transactions both in terms of cost and throughput while preserving close-to-mainnet security thanks to the underlying zero-knowledge proofs that are used to validate the correctness of its state changes.

Importantly, contrary to some alternative solutions that we have considered, zkSync is mature enough that it's already live on the Ethereum mainnet and thus it will - obviously - be there for us when the new Golem itself is launched to mainnet.

### zkSync advantages

zkSync supports both ETH itself and potentially any ERC-20-compatible token and transactions on zkSync itself are almost immediate.

Additionally, the transactions fees can be paid in the token that's transferred, eliminating the need for the sender to be in posession of ETH.

Thanks to the underlying technology, namely zkRollup, the validators in zkSync are able to process thousands of transactions in a single block. The hash of such a block and a cryptographic proof that the block is a result of an application of a series of correct state transitions is published to Ethereum blockchain. Alongside it, the delta change resultant from execution of all the included transactions is also published to the blockchain and both the delta and the proof are validated by a smart contract.

The net effect is that, with orders of magnitude smaller costs and much higher transaction throughput zkSync remains almost as secure as the mainnet itself.

## zkSync in Golem

ZkSync is enabled as the default platform to pay for and receive payments for computations in the new Golem. How you'd use it though, depends on whether you're running on testnet or on mainnet.

The current default for providers is running on mainnet and provider accounts are ready to receive both erc20 tokens and zkSync payments out of the box.

On the other hand, because we assume requestors will first start by testing the ground using their just-created apps on the Ethereum testnet, the default network for those nodes is Rinkeby.

When you run `yagna payment fund` \(you don't have to add `--driver=zksync` since it's the default\) on Rinkeby, Golem initializes a new account from our custom faucet \(a service that transfers test tokens to an address that asks for it\) which provides it with test GLM tokens that are already transferred to zkSync. Then all payments are performed through zkSync and in consequence, all the providers receive all the payments to their zkSync accounts.

Of course, you also need to enable your accounts' sender mode, which is done using `yagna payment init --sender`. All this is covered in [our requestor introduction](../requestor-tutorials/flash-tutorial-of-requestor-development.md).

If you're interested in running a requestor on the Ethereum mainnet, to be able to leverage the main pool of Golem providers, please refer to:

{% page-ref page="using-golem-on-mainnet.md" %}

## Further reading

For more information on zkSync, please have a look at its website:

[https://zksync.io/faq/intro.html](https://zksync.io/faq/intro.html)

