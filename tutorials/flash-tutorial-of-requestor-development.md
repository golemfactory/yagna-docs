---
description: >-
  This tutorial shows how to use the new Golem to run an app inside a custom
  Docker image in parallel on multiple providers.
---

# A quick primer into the requestor development

### Prerequisites

At this moment, we support a limited list of platforms. Thus, you'll need one of the following:

* OS X 10.14+
* Ubuntu 18.04 or 20.04

#### Python 3.6+

To verify your currently installed version of python, please run:

```text
python3 --version
```

If you have an older version of python and you'd like to keep that version in your system, consider using [pyenv](https://github.com/pyenv/pyenv). You can use [pyenv-installer](https://github.com/pyenv/pyenv-installer) to facilitate the process.

#### Git

You'll also need the `git` versioning system client so you can clone our repositories. Ensure you have it available with:

```text
git --version
```

#### You don't need any crypto assets

{% hint style="info" %}
You don't need any real ETH or nGNT tokens to start this tutorial. The alpha release works on the Rinkeby testnet and the needed assets are acquired by the daemon in one of the steps below.
{% endhint %}

### Feedback? Help needed?

{% hint style="success" %}
If you'd like to give us feedback, suggestions, have some errors to report or if you got stuck and need help while following our tutorials, please don't hesitate to reach out to us on our Golem Discord: [https://chat.golem.network](https://chat.golem.network)
{% endhint %}

## Running `yagna` daemon

In order to follow our requestor agent tutorial, you'll first need to run the `yagna` daemon. 

First, download the package appropriate for your platform from: [https://github.com/golemfactory/yagna/releases/tag/v0.3.3-alpha.2](https://github.com/golemfactory/yagna/releases/tag/v0.3.3-alpha.2)

Unpack it and put `gftp` and `yagna` binaries somewhere in your PATH \(e.g. copy them to `/usr/local/bin` on unix-like systems\).

Now, you can run the daemon:

```text
yagna service run
```

You'll be asked to confirm the Alpha release's ToS and once you accept them, the daemon will launch. You can skip the confirmation on subsequent runs by adding the `--accept-terms` parameter to the command above.

Once the terms are accepted, the daemon will emit a bunch of log messages confirming its own startup and the startup of several of yagna's components.

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background while you proceed with the tutorial.
{% endhint %}

You can now proceed to [Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key).

#### Warning! Construction zone: errors ahead

{% hint style="danger" %}
You may notice errors while running the yagna daemon or the example script. Some of those errors will be silenced, prevented or handled more gracefully in the future production version. For now, you can usually ignore them, unless of course they make the daemon or the example script crash - or - cause the task itself to fail before completion.
{% endhint %}

Some of the errors you may encounter are:

`[2020-08-11T10:49:17Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID [... url ... ] already registered`

`('prop', 'fail', [...], {'reason': "(500)\nReason: Internal Server Error\nHTTP response headers: \n"})`

`Task exception was never retrieved [... several lines of stack trace ...] {"message":"GSB error: bad request: No service registered under given address"}`    

## Generate the app key

With the daemon running, enter the daemon's directory using another shell and generate the `yagna` app key that will be used by your requestor agent to access yagna's REST API.

```text
yagna app-key create requestor
```

This should produce a 32-character-long hexadecimal app key that you need to note down as it will be needed to run the requestor agent.

In case you lose your app key, you can retrieve it with:

```text
yagna app-key list
```

the value in the `key` column is the key you need.

### Acquire some testnet ETH and nGNT tokens

Instruct the yagna daemon to contact the faucet which issues some ETH and nGNT tokens to the node:

```text
yagna payment init -r
```

and allow some time until it completes its job.

{% hint style="warning" %}
Due to the fact that our example uses the Rinkeby Ethereum testnet, the transactions that add ETH and nGNT to the requestor node's address need to be mined and confirmed there. It may take several minutes until that's completed.
{% endhint %}

You can verify whether you already have the funds with:

```text
yagna payment status
```

If it doesn't succeed after a few minutes, re-run the `payment init` command above and check again after a few more minutes.

## Running the requestor

Now you have the `yagna` daemon running, you may proceed with running a task as a requestor.

### Get the environment set up

Ensure you're running python &gt;= 3.6 and you have the `venv` module installed.

Prepare a virtual environment for the tutorial script:

```text
python3 -m venv ~/.envs/yagna-python-tutorial
source ~/.envs/yagna-python-tutorial/bin/activate
```

Install the dependencies:

```text
pip install yapapi certifi
```

### Get the requestor agent's code

Check out or download the `yapapi` repository:

```text
git clone https://github.com/golemfactory/yapapi.git
```

### Set the yagna app key

In order for the requestor agent to connect with the yagna daemon, you need to provide it with the previously-generated app key. You do that by setting the appropriate environment variable to a value acquired in the "[Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key)" step above:

```text
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

The example we're showcasing here resides in the `examples/blender` directory within `yapapi`'s codebase so, ensure that you're in the checked-out repository's directory and run:

```bash
cd yapapi/examples/blender
python3 ./blender.py
```

If everything works as expected, you should see some messages that confirm agreements being struck between your requestor node and the providers in our testnet which will look something like:  
  
`('agr', 'create', '1a68db7e-b11b-45b0-872d-8b4f28f2c492', {'provider_idn': Identification(name='2rec-ubuntu', subnet_tag='testnet')})`

Afterwards, you should see the work dispatched to providers with lines starting with `new batch !!!` and subsequently confirmations of tasks getting accepted by our example requestor agent:

`('task', 'accept', None, {'result': None})`

The example in question generates six discrete jobs for providers to execute so after those six activities are completed and results returned, the whole task is finished.

`progress= {'done': True}`

{% hint style="success" %}
Yay! With this, you have completed your first job as a requestor in the new Golem network!
{% endhint %}

You can verify that it's indeed done by examining the generated output files which are `PNG` images with the selected frames of the rendered animation that should appear in the directory from which you ran the example script.

Here is an example rendered frame, provided here for reference:

![](../.gitbook/assets/output_0.png)

## Next steps

So, you have successfully completed your first task as a requestor on the new Golem network and would like to know and do more?

If you'd like to understand, extend and play around with our example, please consult:

{% page-ref page="requestor-tutorial.md" %}

On the other hand, if you'd like to deploy your own dockerized apps to our alpha testnet, have a look at:

{% page-ref page="convert-a-docker-image-into-a-golem-image.md" %}

