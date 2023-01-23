---
description: A minimal example of a functional Golem requestor agent
---

# Task Example 0: Hello World!

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Task execution
* Retrieving command output from provider's exe unit
{% endhint %}

## Prerequisites

The only assumption made in this article is that you have some familiarity with basic Golem application concepts. Here's a good starting point to learn about these:

{% content-ref url="../golem-application-fundamentals/" %}
[golem-application-fundamentals](../golem-application-fundamentals/)
{% endcontent-ref %}

Here are the prerequisites in ---
description: A minimal example of a functional Golem requestor agent
---

# Task Example 0: Hello World!

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Task execution
* Retrieving command output from provider's exe unit
  {% endhint %}

## Prerequisites

The only assumption made in this article is that you have some familiarity with basic Golem application concepts. Here's a good starting point to learn about these:

{% content-ref url="../golem-application-fundamentals/" %}
[golem-application-fundamentals](../golem-application-fundamentals/)
{% endcontent-ref %}

Here are the prerequisites in case you'd like to follow along and/or experiment with the code presented in this article:

* you have a local `yagna` node set up (instructions can be found here: [Requestor development: a quick primer](../flash-tutorial-of-requestor-development/))
* you have the JS Golem high-level API set up on your machine (instructions here: [Run first task on Golem](../flash-tutorial-of-requestor-development/run-first-task-on-golem.md))

## Requestor agent code

Let's jump straight to the example:

{% hint style="info" %}
This example uses the standard VM runtime.
{% endhint %}

```javascript
(async function main() {
  const executor = await TaskExecutor.create("9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae");
  await executor.run(async (ctx) => console.log((await ctx.run("echo 'Hello World'")).stdout));
  await executor.end();
})();
```

That's all we need in order to run a task on Golem!

### How does it work?

Here's the flow diagram of all the interactions that need to happen between the requestor and the provider(s) in order for a task to be completed:

![Sequence diagram of requestor -> provider interactions](../../.gitbook/assets/tutorial-07.jpg)

From a high-level perspective, a successful run of the above program performs the following steps:

1. A single task is scheduled to be executed in the Golem network
2. Once a suitable provider is found in the market, a lightweight VM is launched on that node
3. When the execution environment is ready, the requestor's script is run inside it
4. Once the script is finished, the result is retrieved from the provider and displayed to the terminal

In this minimal example our script consists of a single command: the Linux `echo` utility. This program returns `Hello World` string.

Let's move on to exploring our example code!

## The main() function

This function is our program's entry point and it performs three steps:

1. Create `TaskExecutor` instance
2. Defining and execute `Worker` function
3. End `TaskExecutor` object

### Task Executor

The executor can be created by passing appropriate initial parameters such as package, budget, subnet tag, payment driver, payment network etc.
One required parameter is a package. This can be done in two ways. First by passing only package image hash, e.g.
```javascript
const executor = await TaskExecutor.create("9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae"); 
```
Or by passing some optional parameters, e.g.
```javascript
const executor = await TaskExecutor.create({
  subnetTag: "public",
  payment: { driver: "erc-20", network: "sepolia" },
  package: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
});
```

Currently, Golem is using a public repository to store both official and community-authored VM images. Once an image is uploaded to this repository it can be referred to by its hash.

This is what we're making use of here - by setting `package` parameter, we're getting a payload definition for our providers. The only input we must provide at this point is the image hash. In the case of this example we're using a pre-uploaded, minimal image based on Alpine Linux.
Instead of passing image hash, we can also pass the `Package` instance created by `Package.create` utility class. In the current version we can only support VM ExeUnit Runtime.  

{% hint style="info" %}
If you'd like to learn about creating and uploading Golem images yourself, take a look at this article: [VM runtime: How to convert a Docker image into a Golem image?](../vm-runtime/convert-a-docker-image-into-a-golem-image.md)
{% endhint %}

### `Worker` function

The executor provide API to execute some task on the Golem network. You can run simple worker function by:

```javascript
await executor.run(async (ctx) => console.log((await ctx.run("echo 'Hello World'")).stdout));
```

The `Worker` function pass to `executor.run()` is what defines the interaction between our requestor node and each provider computing one or more of our tasks. It's called once per provider node with which our requestor has struck an agreement.

`WorkContext` gives us a simple interface to construct a script that translates directly to commands interacting with the execution unit on provider's end. Using this object we can schedule commands such as transferring files, running programs etc.

In the case of this example our entire script consists of a single command which is the call to `ctx.run`. This means that, once committed, the provider's exe unit will receive an instruction to make a call to `/bin/sh -c echo "Hello World"`.

{% hint style="warning" %}
Commands run with `ctx.run` are executed in `/bin/sh` shell by default. This means you have to be sure that vm image contain this shell, otherwise you have to specify the full binary path or run the command through a shell manually (for example: `/bin/node ...`).
{% endhint %}

When the worker `Promise` is resolved, we get a `Result` object that contains the `stdout` and `stderr` of the specified command.

### Termination of an executor instance

Termination of contracts, payment processing, etc.

```js
await executor.end();
```

## All done!

That's all there is to the example!

To run it on your local machine make sure you have a `yagna` node running and set up as a requestor (take a look here in case of any doubts: [Requestor development: a quick primer](../flash-tutorial-of-requestor-development/)). You can then issue the following command:

```
YAGNA_APPKEY={your_appkey_here} node ./hello.js
```

This assumes you're in the directory which contains the `hello.js` file. You'll also need to provide your node's actual app key. If everything went fine you should see a log similar to the one below:

```
2023-01-23 13:45:49.645+01:00 [yajsapi] info: Agreement proposed to provider 'someone'
2023-01-23 13:45:49.650+01:00 [yajsapi] info: Agreement confirmed by provider 'someone'
2023-01-23 13:45:51.261+01:00 [yajsapi] info: Task 1 sent to provider 'someone' Data: undefined
Hello World

2023-01-23 13:45:53.992+01:00 [yajsapi] info: Task 1 computed by provider 'someone'. Data: undefined
2023-01-23 13:45:56.537+01:00 [yajsapi] info: Invoice accepted from 'someone'
2023-01-23 13:45:59.408+01:00 [yajsapi] info: Computation finished in 7.2s
```

`Helo World` is the result we received from executing the `echo "Hello World"` command inside our provider's exe unit.

Ready for a more complex scenario? Take a look at the next article which implements a rudimentary hash cracker using Golem network.
