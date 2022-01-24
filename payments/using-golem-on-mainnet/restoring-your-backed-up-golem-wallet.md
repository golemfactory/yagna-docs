---
description: Setting up a new yagna instance to use a saved keystore file.
---

# Restoring a backed-up wallet

If, for whatever reason, your Golem wallet is destroyed or corrupted e.g. you moved on to a new machine and forgot to take move Golem's installation with it, you'll be faced with the necessity to recover your wallet from your previously backed-up keystore file.

To restore your wallet, first start with a fresh yagna install:

```
curl -sSf https://join.golem.network/as-requestor | bash -
```

{% hint style="warning" %}
The above line assumes you're a requestor on a unix-like platform (Linux or Mac). If that's not the case, you should use an installation procedure appropriate for your platform. Please refer to the [installation section of our requestor development primer](../requestor-tutorials/flash-tutorial-of-requestor-development/#running-the-yagna-daemon) or to the [analogous part of the introduction for providers](../../provider-tutorials/provider-tutorial.md#installation).
{% endhint %}

Once yagna is installed, run it with:

```
yagna service run
```

Now, as usual, leave the daemon running in the background and proceed with the rest of the process in another terminal window.

### Retrieve your keystore

Here you'll need the key.json file you had previously backed up. Do whatever you need to restore it - e.g. decrypt it if you previously encrypted it. For the process to work, it must be the same plain-text json file that yagna originally exported.

Be sure that your `key.json` file is in your current working directory and run:

```
yagna id create --from-keystore ./key.json
```

This should create a new identity in yagna based on your backed-up wallet. If the private key that you just imported is password-protected, the message that you receive on a successful import will include `isLocked: true` and means that you'll need to unlock the key later on before it can be used by yagna.

On the other hand, if the message reads: `isLocked: false`, it means that you're using an uprotected keystore file.

### Set the new identity as yagna's default

**1.** Using the Ethereum address of your backed-up wallet, run:

```
yagna id update --set-default 0x-the-address
```

**2. STOP YOUR YAGNA DAEMON**

(just press Ctrl-C in the console that's running `yagna service run` and wait for the daemon to exit)

**3.** Remove `yagna`'s accounts configuration file

{% tabs %}
{% tab title="Ubuntu" %}
```
rm $HOME/.local/share/yagna/accounts.json
```
{% endtab %}

{% tab title="mac OS X" %}
```
rm $HOME/Library/Application\ Support/GolemFactory.yagna/accounts.json
```
{% endtab %}

{% tab title="Windows" %}
```
del %APPDATA%\GolemFactory\yagna\data\accounts.json
```
{% endtab %}
{% endtabs %}

**4. Start your yagna daemon again** (as usual, do it in a separate command line terminal and allow it to run in the background)

```
yagna service run
```

**5.** Ensure yagna is using your newly-restored wallet

```
yagna id show
```

The `nodeId` property should display the Ethereum address of your backed-up wallet.

{% hint style="warning" %}
If your key is password-protected, you'll need to unlock it before it can be used for payments. In such case, `yagna id show` command above will report:

`isLocked: true`

To unlock your key, you can use:

```
yagna id unlock
```

and supply the key's password.

This will unlock your key and `yagna` will be able to use it for outgoing payments. You can confirm that the operation succeeded by verifying that the output now reports:

`isLocked: false`

You'll need to unlock your key each time you start your yagna daemon because, for security reasons, yagna does not save your passphrase anywhere.
{% endhint %}

### Make sure your yagna application key is bound to the correct account

If you have used `yagna` before, you have probably already created an application key (the key that the requestor agent uses to connect to the `yagna` daemon).

In that case, after you import your Ethereum mainnet key, you need to re-create Yagna's application key, as the previous one is now bound to your old (rinkeby) key:

```
 yagna app-key create requestor-mainnet
```

The name (`requestor-mainnet`above) is not important as long as it doesn't collide with the existing one (assuming it was just `requestor`).

After you have done that run:

```
yagna app-key list
```

and verify that in the table like the one below, your new app-key is bound to your mainnet Ethereum address

```
┌─────────────────────┬────────────────┬───────────────────────────┬───────────┬──────────────────────────────┐
│  name               │  key           │  id                       │  role     │  created                     │
├─────────────────────┼────────────────┼───────────────────────────┼───────────┼──────────────────────────────┤
│  requestor-mainnet  │  your-app-key  │  0x-your-mainnet-address  │  manager  │  2021-07-06T11:41:52.252257  │
└─────────────────────┴────────────────┴───────────────────────────┴───────────┴──────────────────────────────┘
```

Lastly, remember to set the new app-key in your environment (or in an other way you supply the app key to your requestor agent app).
