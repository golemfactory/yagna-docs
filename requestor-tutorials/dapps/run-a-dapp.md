---
description: Quick start to running your first decentralized application on Golem
---

# Quick start

## What's in it for me?

By following this tutorial, you'll see how easy it is to deploy web applications to Golem.

You should be able to complete it regardless of your level of experience. However, it will help if
you have some fluency using basic unix tools like `curl` or `git` and are not afraid of
running console commands.


## Prerequisites

To launch applications on Golem, you request computational resources from the network. 
Therefore, you need the following prerequisites prior to execution:

* a running `yagna` daemon (v0.12 or higher)
* your requestor app key

Setting these up is a part of the tutorial linked below.
You only need to complete the first part, and omit "Run first task on Golem".
Once you have your yagna daemon running and your application key copied, feel free to proceed here.

{% content-ref url="flash-tutorial-of-requestor-development/" %}
[flash-tutorial-of-requestor-development](flash-tutorial-of-requestor-development/)
{% endcontent-ref %}

Please also ensure you have `curl` installed on your system.

```shell
curl --version
```

## Installation

### Get the virtual environment set up

It's best to run any Python applications in a virtual environment so as not to clutter your system's Python installation with unnecessary packages.

Ensure you're running Python >= 3.8 and you have the `venv` module installed (it's normally included in the Python distribution).

Prepare a virtual environment for the tutorial script:

```bash
python3 -m venv --clear ~/.envs/dapps
source ~/.envs/dapps/bin/activate
```

{% hint style="warning" %}
On Windows, you need to replace the above with:
{% endhint %}

```
python -m venv --clear %HOMEDRIVE%%HOMEPATH%\.envs\dapps
%HOMEDRIVE%%HOMEPATH%\.envs\dapps\Scripts\activate.bat
```

### Install `dapp-runner`

The tool which deploys apps to Golem, `dapp-runner` is installable from the PyPi repository with the following command:

```shell
pip install -U pip dapp-runner
```

#### Installation from sources

Alternatively, if you'd like to have the latest package, you can install it from the source.
To do so, clone the repository from GitHub:

```
git clone --recurse-submodules https://github.com/golemfactory/dapp-runner.git
```

and next, install it from there:

```shell
cd dapp-runner
pip install -U pip poetry
poetry install
```

## Running a dApp on Golem

### Get the sample app 

```
curl https://raw.githubusercontent.com/golemfactory/dapp-store/cb780de6d2c3e42beaa1195c418242d0cc7701b7/apps/webapp.yaml > webapp.yaml
```

### And the default config file

```
curl https://raw.githubusercontent.com/golemfactory/dapp-runner/main/configs/default.yaml > config.yaml
```

### Run the app 

Having the above setup complete, you can verify it by running a sample application that comes together with `dapp-runner` repository using the following commands:

```shell
YAGNA_APPKEY=<your_key> dapp-runner start --config config.yaml webapp.yaml 
```

Once the app is deployed on Golem, you should see a line reading:

```json
{"http": {"local_proxy_address": "http://localhost:8080"}}
```

This means that the app is ready and can be viewed at: [http://localhost:8080](http://localhost:8080)

(The port on your machine may be different)

***That's it :)***

Now that you've been able to experience launching decentralized apps on Golem, you might wish to learn what it takes to build one yourself.

{% content-ref url="your-first-golem-dapp.md" %}
[your-first-golem-dapp](your-first-golem-dapp.md)
{% endcontent-ref %}
