---
description: >-
  Alternatively to running yagna from binaries, especially if you're an
  adventurous type, you might want to run it directly from sources.
---

# Running the yagna daemon from sources

Running from sources allows you to have a closer look at its internals and to try all the latest features while they're being developed. It's important to note that, unless you _really_ know what you're doing, you'll be better off using our bundled binaries.

To run `yagna` from sources, you'll need to have `rust` development environment installed - it will be needed to run the `yagna` daemon itself. If you don't have it, please refer to the docs to install it: [https://www.rust-lang.org/learn/get-started](https://www.rust-lang.org/learn/get-started)

Afterward you'll need to launch the `yagna` service.

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

This command will build `yagna` using the Rust compiler \(which might take a considerable time unless you're working on a really fast machine\) and once it's built, will subsequently launch it.

Once the daemon launches, it will start emitting some debug messages among which one of the first ones will look like:

`[2020-07-16T12:11:33Z INFO yagna] Starting yagna service!` .

There you go! You have successfully started the yagna daemon and can use it to connect to the Golem network, run our examples and develop your own Golem apps.

{% hint style="warning" %}
Remember that, when running from sources, the `yagna` command must be replaced with `cargo run`in any of the examples we provide elsewhere in this documentation. E.g. instead of: `yagna app-key list` you'd run: `cargo run app-key list`.
{% endhint %}

## Build the `gftp` binary

If you're running `yagna` from source, then you won't have the `gftp` binary around and you need to also build it yourself. To do so, once again, go to your `yagna` source directory and execute:

```bash
cd core/gftp
cargo install --path .
```

This will build and install the `gftp` binary for you.

{% hint style="success" %}
Your `yagna` daemon is now ready!
{% endhint %}

