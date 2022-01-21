---
description: ensuring safety of your Golem funds.
---


# Backing up your Golem wallet

As you're probably aware, in the Ethereum universe, your funds are only as secure as the private key for the account that holds them. Because of that, to ensure that you don't lose access to your GLM/ETH tokens stored on your Golem account, it's crucial for you to be able to back-up your Golem wallet and store the key in a safe storage, separate from the node itself.

## Simple, unsafe export

To create a backup of your Golem wallet, export the keystore with:

```text
yagna id export --file-path=./key.json
```

The resultant `key.json` file in the directory you ran the command from will contain the private key for your Golem wallet.

{% hint style="danger" %}
Keep in mind that saving your wallet this way results in a creation of an unprotected keystore file.

Whoever enters into posession of your `key.json` file will have complete control over the wallet and any funds therein. Unless you're really sure that you want this, use the password-protected export described below.
{% endhint %}

## Password-protected keystore

Better yet, create a password-encrypted keystore. Yagna daemon allows it and it fundamentally improves the security of the funds kept in that exported wallet.

### Verify the currently used key

First, make sure that the key you're securing is indeed the one yagna is currently configured to use:

```
yagna id show
```

The result should be something like:

```
---
Ok:
  alias: ~
  isDefault: true
  isLocked: false
  nodeId: "0x-the-hexadecimal-ethereum-address"
```

It's important to verify that the command shows you `isDefault: true` and `isLocked: false` and that the address shown by `nodeId` is the address you're expecting to see. `isDefault: true` means that the key for the address is currently in use by yagna and `isLocked: false` confirms that the private key is currently unlocked and accessible to the yagna node. [@todo verify what happens when it's true]

### Lock the key

To lock the key using your own passphrase, issue the following command:

```
$ yagna id lock --new-password
```

You'll be asked for the passphrase twice and if the entries match, you'll receive a confirmation of the lock operation:

```
---
Ok:
  alias: ~
  isDefault: true
  isLocked: true
  nodeId: "0x-the-hexadecimal-ethereum-address"
```

Notice that `isLocked` is now set to `true`.

{% hint style="warning" %}
Remember to save your passphrase somewhere safe as losing it will make it impossible to unlock the key later on.
{% endhint %}

### Export the key

Now, issue the same export command that you'd use for an unprotected keystore:

```
yagna id export --file-path=./key.json
```

### Unlocking on yagna restart

An, arguably positive, side effect of locking the key that way is that a `yagna id unlock` command will now be needed each time the yagna daemon is restarted. This means that no one can use your yagna node as a requestor without knowing your passphrase.

### Reverting to an unprotected key

If for some reason you'd like to revert to an unprotected yagna key, unlock it using your saved passphrase and they lock it again using en empty one, that is run:

```
yagna id lock --new-password
```

and input an empty password (just press "Enter") twice. Now, yagna will start with an unlocked key by default again.

## Verify the resultant keystore file

Once the file is created, examine its contents and ensure that the `address` property in it is identical to the address of your node's Ethereum address. Normally there's no reason for this field to differ - but treat this step as a redundant check to ensure that you have backed up what you intended to back-up.

To make it easier, here's a possible check:

```
$ cat ./key.json | grep address
```

To be entirely sure that your backup is correct, launch a completely new, separate yagna node from scratch on another machine and [verify that it's possible to restore your wallet](restoring-your-backed-up-golem-wallet.md) using this newly created keystore file.

{% hint style="danger" %}
Ensure you store that key file in a safe place. In case your Golem wallet gets corrupted or lost, if you don't have the backup, your funds will be lost forever.

Likewise, consider encrypting or password-protecting the keystore file so that someone who'd take hold of the file won't automatically be able to take control of your funds. We have included appropriate instructions above.
{% endhint %}
