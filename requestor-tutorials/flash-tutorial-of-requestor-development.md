---
description: >-
  This tutorial shows how to use the new Golem to run an app inside a custom
  Docker image in parallel on multiple providers.
---

# Requestor development: a quick primer

## Prerequisites

#### Platforms

This is our very first Alpha reveal. Therefore, temporarily, Golem only supports a limited list of platforms. These are those:

* OS X 10.14+
* Ubuntu 18.04 or 20.04

#### Languages

{% hint style="warning" %}
If you are JS developer, please click to **NodeJS** tab
{% endhint %}

{% tabs %}
{% tab title="Python" %}
#### Python 3.6+

To verify your currently installed version of python, please run:

```text
python3 --version
```

If you have an older version of python and you'd like to keep that version in your system, consider using [pyenv](https://github.com/pyenv/pyenv). You can use [pyenv-installer](https://github.com/pyenv/pyenv-installer) to facilitate the process.
{% endtab %}

{% tab title="NodeJS" %}
{% hint style="danger" %}
Please bear in mind that our **JS/TS** API is an early alpha release and not nearly as refined as the Python one.
{% endhint %}

#### NodeJS 12.13.0+

To verify your currently installed version of node, please run:

```text
node --version
```

If you have an older version of node and you'd like to keep that version in your system, consider using [nvm](https://github.com/nvm-sh/nvm). You can install it using the instructions from: [https://github.com/nvm-sh/nvm\#install--update-script](https://github.com/nvm-sh/nvm#install--update-script)  
  
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

#### No crypto assets needed \(for now!\)

{% hint style="info" %}
Alpha lives on the Rinkeby Testnet. You don't need any real ETH or GNT tokens to start this tutorial. You also don't need to do anything to get test tokens! These test assets are acquired by the daemon in one of the steps below.
{% endhint %}

### Can we help you? Do you have feedback for Golem?

{% hint style="success" %}
If you'd like to give us feedback, suggestions, have some errors to report or if you got stuck and need help while following our tutorials, please don't hesitate to reach out to us on our Golem Discord: [https://chat.golem.network](https://chat.golem.network)
{% endhint %}

## Running the `yagna` daemon

{% hint style="info" %}
_Yagna is the main service of the new Golem that's responsible for keeping connections with all the other nodes in the network._
{% endhint %}

In order to follow our requestor agent tutorial, you'll first need to run the `yagna` daemon. 

#### Easy installation

You can install it using our helper script like this:

```text
curl -sSf https://join.golem.network/as-requestor | bash -
```

You might be asked to modify your PATH afterwards.

#### Manual installation

Alternatively, if you'd like to have more control over the installation process, or would like to choose where the binaries end up, you can do that manually.

First, download the requestor package - prefixed `golem-req` - appropriate for your platform from: [https://github.com/golemfactory/yagna/releases/tag/pre-rel-v0.4.0-f4e85cd3](https://github.com/golemfactory/yagna/releases/tag/pre-rel-v0.4.0-f4e85cd3)

Unpack it and put the binaries contained within somewhere in your PATH \(e.g. copy them to `/usr/local/bin` on unix-like systems\).

### Confirm the installed daemon's version

Once binaries are installed, confirm that you're running the latest Golem release:

```text
yagna --version
```

It should output: `yagna 0.4.0-f4e85cd3`

### Purge the stale working directories

If you had run a previous version of `yagna` in the past, you'll need to purge its working directories since our newest version is incompatible with the old database structure:

{% tabs %}
{% tab title="Ubuntu" %}
```text
rm -rf $HOME/.local/share/yagna
```
{% endtab %}

{% tab title="mac OS X" %}
```text
rm -rf $HOME/Library/Application\ Support/GolemFactory.yagna
```
{% endtab %}
{% endtabs %}

### Run the daemon

Now, you can run the daemon:

```text
yagna service run
```

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background while you proceed with the tutorial.
{% endhint %}

You can now proceed to [Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key).

#### Warning! Construction zone: errors ahead

{% hint style="danger" %}
You may notice errors while running the yagna daemon or the example script. **Some of those errors will be silenced, prevented or handled more gracefully in the future production version.** For now, you can usually ignore them, unless of course, they make the daemon or the example script crash - or - cause the task itself to fail before completion.
{% endhint %}

Some of the errors you may encounter are:

`[2020-08-11T10:49:17Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID [... url ... ] already registered`

`Task exception was never retrieved [... several lines of stack trace ...] {"message":"GSB error: bad request: No service registered under given address"}`

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

### Enable the daemon as a requestor

You need the following command to enable the daemon as a requestor.

What it also does under the hood, it also checks for funds on your requestor node and if needed, contacts the faucet which issues some ETH and nGNT tokens to the node.

{% hint style="warning" %}
It needs to be run each time the daemon is started or restarted.
{% endhint %}

```text
yagna payment init -r
```

Once you issue the command, allow some time until it completes its job.

{% hint style="warning" %}
Due to the fact that our example uses the Rinkeby Ethereum testnet, the transactions that add ETH and nGNT to the requestor node's address need to be mined and confirmed there. It may take several minutes until that's completed.
{% endhint %}

You can verify whether you already have the funds with:

```text
yagna payment status
```

If, after a few minutes, you can't see the assets, re-run the `payment init` command above and check again after a few more minutes.

## Running the requestor and your first task on the New Golem Network

Now you have the `yagna` daemon running, you may proceed with running a task as a requestor.

{% tabs %}
{% tab title="Python" %}
### Get the environment set up

Ensure you're running python &gt;= 3.6 and you have the `venv` module installed.

Prepare a virtual environment for the tutorial script:  


```text
python3 -m venv ~/.envs/yagna-python-tutorial
source ~/.envs/yagna-python-tutorial/bin/activate
```

Install the dependencies:

```text
pip3 install -U pip
pip3 install certifi
pip3 install -i https://test.pypi.org/simple/ --extra-index-url=https://pypi.org/simple/ yapapi==0.3.0a2
```

### Get the requestor agent's code

Check out or download the `yapapi` repository:

```text
git clone https://github.com/golemfactory/yapapi.git
```

and make sure you're working on the version corresponding with the latest release:

```text
cd yapapi
git checkout b0.3
```

### Set the yagna app key

In order for the requestor agent to connect with the yagna daemon, you need to provide it with the previously-generated app key. You do that by setting the appropriate environment variable to a value acquired in the "[Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key)" step above:

```text
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

#### Run the example

The example we're showcasing here resides in the `examples/blender` directory within `yapapi`'s codebase so, ensure that you're in the checked-out repository's directory and run:

```bash
cd examples/blender
python3 ./blender.py --subnet-tag devnet-alpha.2
```

Once you launch the example, you should see some messages reflecting the progress of your task's execution - agreement confirmations, task dispatches and finally task completions.

The example in question generates six discrete jobs for providers to execute so after those six activities are completed and results returned, the whole task is finished.

If everything goes right, after what could be anything from half-a-minute to a few minutes, you'll hopefully see the message announcing the successful completion of your assignment including a short summary of what had happened during the execution, which providers took part in the execution and the accumulated GNT cost of the whole task, e.g.:

`Computation finished in 77.5s  
Negotiated 1 agreements with 1 providers  
Provider 'odra' computed 6 tasks  
Total cost: 0.218290307253`
{% endtab %}

{% tab title="NodeJS" %}
### Get the requestor agent's code

Check out or download the `yajsapi` repository:

```text
git clone https://github.com/golemfactory/yajsapi.git
cd yajsapi
git checkout b0.1
```

### Install the dependencies and build the library

```text
yarn && yarn build
```

### Set the yagna app key

In order for the requestor agent to connect with the yagna daemon, you need to provide it with the previously-generated app key. You do that by setting the appropriate environment variable to a value acquired in the "[Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key)" step above:

```text
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

### Run the example task

The example we're showcasing here resides in the `examples/blender` directory within `yajsapi`'s codebase so, ensure that you're in the checked-out repository's directory and run:

```bash
cd examples
yarn
yarn js:blender
```

If everything works as expected, you should see some messages that confirm agreements being struck between your requestor node and the providers in our testnet and then ones that announce work dispatched to providers with lines starting with `new batch !!!` and subsequently confirmations of task completions.

To some more detailed messages, you can run the example with `yarn js:blender -d`. 

The example in question generates six discrete jobs for providers to execute so after those six activities are completed and results returned, the whole task is finished.

`progress= {'done': True}`
{% endtab %}
{% endtabs %}



{% hint style="success" %}
**Yay! With this, you have completed your first job as a requestor in the new Golem network!**
{% endhint %}

#### Output

You can verify that the task is indeed done by examining the generated output files which are `PNG` images with the selected frames of the rendered animation that should appear in the directory from which you ran the example script \(`examples/blender` within the cloned repository's path if you followed the tutorial precisely\) . 

Here is an example rendered frame, provided here for reference:

![](../.gitbook/assets/output_0.png)

#### Payments

Finally, you can verify that the providers have been paid for the work they contributed to get that output to you. First, acquire your Ethereum address - you can do that by running:

```text
yagna app-key list
```

again but this time it's the value in the `id` column that you're interested in. This is your the Ethereum address of your yagna node on the Rinkeby testnet. Once you have that address, head to [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io/) and put the value in the address field there. Afterwards, switch to the "Erc20 Token Txns" tab and you should be able to see your outgoing payments there.

## Next steps

So, you have successfully completed your first task as a requestor on the new Golem network. Are you curious to learn more? Wanna do more stuff?

If you'd like to understand, extend and play around with our example, please consult:

{% page-ref page="requestor-tutorial.md" %}

On the other hand, if you'd like to deploy your own dockerized apps to our alpha testnet, have a look at:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}

