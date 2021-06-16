---
description: >-
  This tutorial shows how to use the new Golem to run an app inside a custom
  Docker image in parallel on multiple providers.
---

# Requestor development: a quick primer

## Prerequisites

#### Platforms

While it's possible that you'll be successful running Golem and this tutorial on other platforms, we officially support the following:

* OS X 10.14+
* Ubuntu 18.04 or 20.04
* Windows

#### Languages

{% hint style="info" %}
If you are a JS developer, please switch to **NodeJS** tab
{% endhint %}

{% tabs %}
{% tab title="Python" %}
#### Python 3.6+

To verify your currently installed version of python, please run:

```text
python3 --version
```

If you have an older version of python and you'd like to keep that version in your system, consider using [pyenv](https://github.com/pyenv/pyenv). You can use [pyenv-installer](https://github.com/pyenv/pyenv-installer) to facilitate the process.

{% hint style="warning" %}
On Windows, you may need to just use `python` instead of `python3`
{% endhint %}
{% endtab %}

{% tab title="NodeJS" %}
#### NodeJS 12.13.0+

To verify your currently installed version of node, please run:

```text
node --version
```

If you have an older version of node and you'd like to keep that version in your system, consider using [nvm](https://github.com/nvm-sh/nvm). You can install it using the instructions from:

* [https://github.com/nvm-sh/nvm\#install--update-script](https://github.com/nvm-sh/nvm#install--update-script) \(Linux/macOS X\)
* [https://github.com/coreybutler/nvm-windows/\#node-version-manager-nvm-for-windows](https://github.com/coreybutler/nvm-windows/#node-version-manager-nvm-for-windows) \(Windows\)

Once you have `nvm` installed on your machine, run:

```text
nvm install v12
```

**Yarn 1.22.3+**

Verify that with:

```text
yarn --version
```

If you don't have `yarn` or need to update, it, please go to: [https://classic.yarnpkg.com/en/docs/install/](https://classic.yarnpkg.com/en/docs/install/) and choose the version appropriate for your operating system.
{% endtab %}
{% endtabs %}

#### Git

You'll also need the `git` versioning system client so you can clone our repositories. Ensure you have it available with:

```text
git --version
```

#### No crypto assets needed \(for now\)

{% hint style="info" %}
During development, you'll most likely want to run your tasks on the Rinkeby Testnet. In that case, you won't need any real ETH or GLM tokens to start this tutorial. These test assets are acquired by the daemon in one of the steps below.

Should you later want to run your tasks on the mainnet, to leverage the potential of all Golem's provider nodes, please have a look at: ["Using Golem on Mainnet"](../../payments/using-golem-on-mainnet.md)
{% endhint %}

### Can we help you? Do you have feedback for Golem?

{% hint style="success" %}
If you'd like to give us feedback, suggestions, have some errors to report or if you got stuck and need help while following our tutorials, please don't hesitate to reach out to us on our Golem Discord: [https://chat.golem.network](https://chat.golem.network)
{% endhint %}

## Running the `yagna` daemon

{% hint style="info" %}
Yagna is the main service of the new Golem that's responsible for maintaining the marketplace and keeping connections with all the other nodes in the network.
{% endhint %}

In order to follow our requestor agent tutorial, you'll first need to run the `yagna` daemon.

#### Easy installation

You can install it using our helper script like this:

```text
curl -sSf https://join.golem.network/as-requestor | bash -
```

You might be asked to modify your PATH afterwards.

{% hint style="warning" %}
On Windows, only the manual installation is supported.
{% endhint %}

#### Manual installation

Alternatively, if you'd like to have more control over the installation process, or would like to choose where the binaries end up, you can do that manually.

First, download the requestor package - prefixed `golem-requestor` - appropriate for your platform from: [https://github.com/golemfactory/yagna/releases/tag/v0.6.4](https://github.com/golemfactory/yagna/releases/tag/v0.6.4)

Unpack it and put the binaries contained within somewhere in your `PATH` \(e.g. copy them to `/usr/local/bin` on unix-like systems\) or add the directory you placed the binaries in to your `PATH`.

{% hint style="warning" %}
It's important for the `yagna` and `gftp` binaries to be available in your shell's PATH, otherwise, you'll encounter issues while continuing the tutorial.
{% endhint %}

### Confirm the installed daemon's version

Once binaries are installed, confirm that you're running the latest Golem release:

```text
yagna --version
```

It should output: `yagna 0.7.0 (3d94857c 2021-06-15 build #155)`

Please also verify that you have the correct version of the `gftp` binary used for file transfers in the Golem network.

```text
gftp --version
```

It should output: `gftp 0.7.0 (3d94857c 2021-06-15 build #155)`

### Run the daemon

Now, you can run the daemon:

```text
yagna service run
```

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background while you proceed with the tutorial.
{% endhint %}

You can now proceed to [Generate the app key](./#generate-the-app-key).

{% hint style="warning" %}
Sometimes, you may notice errors while running the yagna daemon or the example script. Unless they cause your task to be aborted or never finished they are usually no reason to worry. In case of doubt, please consult our [list of "Common Issues" in the Troubleshooting section.](../../troubleshooting/common-issues.md)
{% endhint %}

## Generate the app key

With the daemon running, enter the daemon's directory using another shell and generate the `yagna` app key that will be used by your requestor agent to access yagna's REST API.

```text
yagna app-key create requestor
```

This should produce a 32-character-long hexadecimal app key that **you need to note down** as it will be needed to run the requestor agent.

In case you lose your app key, you can retrieve it with:

```text
yagna app-key list
```

the value in the `key` column is the key you need.

### Get some test GLM tokens

In order to be able to request tasks on Golem, you'll need some GLM tokens \(called tGLM on the rinkeby testnet\) to pay the providers with. Even on the testnet, those tokens are still required but of course you can easily get them issued to you using our tGLM faucet.

That's done using:

```text
yagna payment fund
```

It tells yagna to check for funds on your node and if needed, contacts the faucet which, in turn, issues some tGLM tokens to the node using zkSync.

Once you issue the command, allow some time until it completes its job. You can verify whether you already have the funds with:

```text
yagna payment status
```

If, after a few minutes, you still can't see the tokens, re-run the `yagna payment fund` command above and check again after a few more minutes.

As the last resort, if you suspect that there is a more serious issue with the zkSync payment driver or our faucet, you may wish to completely do away with using it and fall back to the older, on-chain payment driver. In such case, please refer to instructions in [our troubleshooting section](../../troubleshooting/common-issues.md#payment-driver-initialization-issue).

### Enable the daemon as a requestor

As the last step before your requestor node is ready, you'll need to enable the daemon as a requestor.

{% hint style="warning" %}
The command needs to be run each time the daemon is started or restarted.
{% endhint %}

```text
yagna payment init --sender
```

With this completed, you're good to go!

## Next steps

Now you are ready to run computations on Golem:

{% page-ref page="run-first-task-on-golem.md" %}

And by all means, **have fun with Golem!**

