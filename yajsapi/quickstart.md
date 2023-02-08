---
description: Create your own JavaScript application on Golem
---

# Quickstart with Golem

In this article, we'll show you how to launch your first JavaScript app on Golem Network from scratch in 15 minutes.
We have divided the entire article into 3 sections:

* [Preparing the environment](#preparing-the-environment)
* [Installing yagna requestor](#installing-yagna-requestor)
* [Building your first JavaScript application on Golem Network](#building-your-first-javascript-app-on-golem-network)

The first two sections are duplicated with the more elaborate ones described elsewhere in the handbook. However, 
the purpose of this article is not to get into the details, but to show you **how to start working with Golem step by step in minutes**.

If you have a development environment already configured, you can go ahead and skip the first section and move on to the next one.

If you have already installed the yaggna daemon and configured the requestor correctly, go straight to the third section.

## Preparing the environment

{% hint style="info" %}
### Prerequisites
* OS X 10.14+, Ubuntu 18.04 or 20.04 or Windows
* Familiarity with the command line
* Install [Node.js](https://nodejs.org/) version 16.x
* Install [Yarn](https://classic.yarnpkg.com/en/docs/install)  version 1.22.3+
* Install [Git](https://git-scm.com/downloads)
{% endhint %}
  
In this section we will introduce how to run a Simple Node Application on Golem Network. 
The created project will be using a build setup based on pre-built [Golem Image](../requestor-tutorials/vm-runtime) 
and allow us to run Node.js script on [Provider](../introduction/provider).

Make sure you have a 16.x version of Node.js installed: 
```bash
node --version
```

Make sure you have a 1.22.3+ version of Yarn installed:
```bash
yarn --version
```

Make sure you have a Git installed:
```bash
git --version
```

### Installing yagna requestor

To start working with Golem network we need to install `yagna` daemon locally.
In the simplest terms, the daemon allows you to communicate with Golem Network and perform operations on it. 


{% tabs %}
{% tab title="Easy installation" %}
**Easy installation**

You can install it using our helper script like this:

```bash
curl -sSf https://join.golem.network/as-requestor | bash -
```
You might be asked to modify your PATH afterwards.

{% hint style="warning" %}
On Windows, only the manual installation is supported.
{% endhint %}

{% endtab %}
{% tab title="Windows Manual installation" %}
**Manual installation on Windows**

Alternatively, if you can't install in easy way, you will do it manually in the following way:

1. Download the requestor package - prefixed `golem-requestor` - appropriate for your platform from:
[https://github.com/golemfactory/yagna/releases/tag/v0.12.0](https://github.com/golemfactory/yagna/releases/tag/v0.12.0)

2. Unzip the archive to extract the two files:
`yagna.exe` and `gftp.exe`.

3. Copy those files to `C:\Windows\System32`

{% endtab %}

{% tab title="Unix Manual installation" %}
**Manual installation on Unix**

Alternatively, if you can't install in easy way, you will do it manually in the following way:

1. Download the requestor package - prefixed `golem-requestor` - appropriate for your platform from:
   [https://github.com/golemfactory/yagna/releases/tag/v0.12.0](https://github.com/golemfactory/yagna/releases/tag/v0.12.0)

2. Unpack `yagna` and `gftp` binaries and put within somewhere in your PATH (e.g. copy them to /usr/local/bin on Unix-like systems) 
or add the directory you placed the binaries in to your PATH

{% endtab %}
{% endtabs %}

Verify if `yagna` available in command line:
```bash
yagna --version
```
It should output: `yagna 0.12.0 (37060503 2022-12-02 build #251)`

Verify if `gftp` available in command line:
```bash
gftp --version
```
It should output: `gftp 0.12.0 (37060503 2022-12-02 build #251)`

If the above commands executed correctly, congratulations you have just installed the `yagna` daemon in your environment.

{% hint style="info" %}
If you have encountered problems, or would you like to learn more details about the requestor and `yagna `installation, please take a look in here:
[How to install requestor tutorial](../requestor-tutorials/flash-tutorial-of-requestor-development)
{% endhint %}

### Configure requestor and fund your wallet
To start using Golem Network you need a key, which will be also be the address of your wallet. 
For the purposes of this tutorial we are using testnet. To generate a key and fund your wallet follow these steps:

#### Firstly, start the daemon

To perform any operations on the Golem Network the `yagna` daemon must be running. To do this, open a command line window and type:
```bash
yagna service run
```

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background while you proceed with the tutorial.
{% endhint %}

{% hint style="info" %}
If you have encountered problems please take look on [Run the daemon](../requestor-tutorials/flash-tutorial-of-requestor-development#run-the-daemon) section
{% endhint %}

#### Secondly, generate the app key (wallet)
To use the network you must have your own unique key(wallet) for which is used for billing. To generate the key,
make sure you have running `yagna` daemon from the [previous step](#firstly-start-the-daemon), leave it running in the background 
and in a separate command line window type in:

```bash
yagna app-key create requestor
```
**Please, note the key down**

#### Thirdly, get some funds

In order to be able to request tasks on Golem Network, you'll need some GLM tokens. To get some funds on testnet, type in:
```bash
yagna payment fund
```

Once you run the command, give some time to transfer funds to your wallet. You can verify whether you already got the funds with:
```bash
yagna payment status
```

{% hint style="info" %}
If you have encountered problems, or would you like to learn more details about the funding process, please take a look in here:
[How to get some GLM tokens](../requestor-tutorials/flash-tutorial-of-requestor-development#get-some-test-glm-tokens)
{% endhint %}

## Building your first JavaScript app on Golem Network

Congratulations you are now ready to start building your first JavaScript app on the Golem Network.
To do this, create a new node project by typing in the command line:

```bash
mkdir golem-tutorial-js
cd golem-tutorial-js
yarn init golem-tutorial-js
```

Add `yajsapi` to your project:
```bask
yarn add yajsapi
```

Create `index.js` file in the main folder and import `TaskExecutor` from `yajsapi`

```js
import { TaskExecutor } from "yajsapi";
```

After importing `TaskExecutor` we have to create IIAFE (Immediately Invoked Async Function Expression) in index.js body, 
because `TaskExecutor` provides async methods:

```js
(async () => {
    //... Function body in here
})();
```

In our body function first we have to create executor using factory method [Executor.create()](./docs/classes/executor_executor.TaskExecutor.md#create). 
As a parameter we will provide pre-built image hash with Node.js.

```js
const executor = await TaskExecutor.create("529f7fdaf1cf46ce3126eb6bbcd3b213c314fe8fe884914f5d1106d4");
```

{% hint style="info" %}
For the testing purposes we are providing a couple of pre-built images:
 * Node `529f7fdaf1cf46ce3126eb6bbcd3b213c314fe8fe884914f5d1106d4`
 * Python 3.6 `6539a63fecfb4ce98bc838ab2de71c6f4d36e1ee5945fbd8f1165c48`
{% endhint %}
