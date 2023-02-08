---
description: Create your own task application on Golem
---

# Quickstart with Golem

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
```
node --version
```

Make sure you have a 1.22.3+ version of Yarn installed:
```
yarn --version
```

Make sure you have a Git installed:
```
git --version
```

### Installing yagna requestor

To start working with Golem network we need to install `yagna` daemon locally.
In the simplest terms, the daemon allows you to communicate with Golem Network and perform operations on it. 


{% tabs %}
{% tab title="Easy installation" %}
**Easy installation**

You can install it using our helper script like this:

```
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
```
yagna --version
```
It should output: `yagna 0.12.0 (37060503 2022-12-02 build #251)`

Verify if `gftp` available in command line:
```
gftp --version
```
It should output: `gftp 0.12.0 (37060503 2022-12-02 build #251)`

If the above commands executed correctly, congratulations you have just installed the `yagna` daemon in your environment.

{% hint style="info" %}
If you have encountered problems, or would you like to learn more details about the requestor and `yagna `installation, please take a look in here:
[How to install requestor tutorial](../requestor-tutorials/flash-tutorial-of-requestor-development)
{% endhint %}

### Configure requestor