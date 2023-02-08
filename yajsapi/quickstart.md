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

### Installing yagna daemon and configure it as requestor  

To start working with Golem network we need to install `yagna` daemon locally.
In the simplest terms, the daemon allows you to communicate with Golem Network and perform operations on it. 


{% tabs %}
{% tab title="MacOS" %}
**Python 3.6+**

To verify your currently installed version of python, please run:

```
python3 --version
```

If you have an older version of python and you'd like to keep that version in your system, consider using [pyenv](https://github.com/pyenv/pyenv). You can use [pyenv-installer](https://github.com/pyenv/pyenv-installer) to facilitate the process.

{% hint style="warning" %}
On Windows, you may need to just use `python` instead of `python3`
{% endhint %}
{% endtab %}
{% endtabs %}