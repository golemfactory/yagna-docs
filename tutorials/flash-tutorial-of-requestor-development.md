---
description: Copy and paste quick tutorial
---

# A quick primer into the requestor development

This is complete tutorial describing the creation and execution of a Golem requestor agent.

The tutorial shows how to create a requestor agent that performs [Blender](https://www.blender.org/) rendering in parallel on multiple providers with the use of Blender's docker image. 

TO DO: 

show gvmkit usage

testnet support in python code

## Running `yagna` daemon

In order to follow our requestor agent tutorial, you'll first need to run the `yagna` daemon. 

First, download the package appropriate for your platform from: [https://github.com/golemfactory/yagna/releases/tag/v0.3.0a](https://github.com/golemfactory/yagna/releases/tag/v0.3.0a)

Unpack it and put `gftp` and `yagna` binaries somewhere in your PATH \(e.g. copy them to `/usr/local/bin` on unix-like systems\).

Once that's done, run the daemon:

```text
yagna service run
```

The daemon will emit a bunch of log messages confirming its startup and the startup of several of yagna's components.

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background while you proceed with the tutorial.
{% endhint %}

You can now proceed to [Generate the app key](flash-tutorial-of-requestor-development.md#generate-the-app-key).

### Running `yagna` daemon from sources

Alternatively, especially if you're an adventurous type, you might want to run `yagna` from sources. For this, you'll need to have `rust` development environment installed - it will be needed to run the `yagna` daemon itself. If you don't have it, please refer to the official docs to install it: [https://www.rust-lang.org/learn/get-started](https://www.rust-lang.org/learn/get-started) 

Afterwards, you'll need to launch the `yagna` service.

First, clone the `yagna` repository from: [https://github.com/golemfactory/yagna/](https://github.com/golemfactory/yagna/releases/tag/vm-poc)

```python
git clone https://github.com/golemfactory/yagna.git
```

Once you have it cloned and checked out, enter its directory and: first, copy the template environment file onto a proper .env file:

```bash
cp .env-template .env
```

 then run:

```text
cargo run service run
```

This command will build `yagna` using the Rust compiler \(which can take a considerable time unless you're working on a really fast machine\) and once it's built, will subsequently launch it.

Once the daemon launches, it will start emitting some debug messages among which one of the first ones will look like: 

`[2020-07-16T12:11:33Z INFO yagna] Starting yagna service!` .  

There you go! Leave the shell with the yagna service running and you're ready for the following steps.

#### Build the `gftp` binary

If you're running `yagna` from sources, you won't have the `gftp` binary around and you need to also build it yourself. To do so, once again, go to your `yagna` source directory and execute:

```bash
cd core/gftp
cargo install --path .
```

This will build and install the `gftp` binary for you.

## Generate the app key

With the daemon running, enter the daemon's directory using another shell and generate the `yagna` app key that will be used by your requestor agent to access yagna's REST API.

{% tabs %}
{% tab title="binaries" %}
```bash
yagna app-key create requestor
```
{% endtab %}

{% tab title="source" %}
```
cargo run app-key create requestor
```
{% endtab %}
{% endtabs %}

This should produce a 32-character-long hexadecimal app key that you need to note down as it will be needed to run the requestor agent.

In case you lose your app key, you can retrieve it with:

{% tabs %}
{% tab title="binaries" %}
```bash
yagna app-key list
```
{% endtab %}

{% tab title="source" %}
```
cargo run app-key list
```
{% endtab %}
{% endtabs %}

the value in the `key` column is the key you need.

### Ensure you have some ETH and GNT tokens ready

{% tabs %}
{% tab title="binaries" %}
```bash
yagna payment init -r
```
{% endtab %}

{% tab title="source" %}
```
cargo run payment init -r
```
{% endtab %}
{% endtabs %}

and allow a few minutes for the faucet to do its job.

You can verify whether you already have the funds with:

{% tabs %}
{% tab title="binaries" %}
```text
yagna payment status
```
{% endtab %}

{% tab title="source" %}
```
cargo run payment status
```
{% endtab %}
{% endtabs %}

If it doesn't succeed after a few minutes, re-run the `payment init` command above and check again after a few more minutes.

### 

## Running the requestor

To run the above code:

* prepare virtual environment for the tutorial script, e.g. with `virtualenvwrapper`:

```text
mkvirtualenv -p python3 yagna-python-tutorial
```

* and install the dependencies:

```text
pip install yapapi certifi
```

* copy the above example python requestor code and place it as `example.py` in the same directory as your blender scene file
* if you're using a scene file with a different name than `cubes.blend` above make sure that your example code refers to your scene file
* set the `YAGNA_APPKEY` to the app key that you received after you have created the yagna app key

```text
export YAGNA_APPKEY=insert-your-32-char-app-key-here
```

* and run the requestor agent:

```text
python3 ./example.py
```



