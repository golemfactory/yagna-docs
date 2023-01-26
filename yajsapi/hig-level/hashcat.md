---
description: List of actions needed to execute the hashcat example.
---

# Task Example 2: Hashcat on Golem

This section contains steps you need to execute in order to run our hashcat password-recovery example. As this tutorial is designed to inspire you to create your own Golem applications, we will explain all the needed details of Golem application implementation.

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Task execution
* Parallel task execution on multiple provider
* Submitting multiple task sequences to a single`Golem` engine
* Setting timeout for commands run on a provider
* Reading output from commands run on a provider
* File transfer to/from provider's exe unit
{% endhint %}

## What is hashcat?

[_Hashcat_](https://hashcat.net/hashcat/) is a command-line utility that finds unknown passwords from their known hashes.

{% hint style="info" %}
Hashcat is a very powerful tool. It supports 320 hashing algorithms and 5 different attack types. We will use only the "phpass" algorithm and a simple brute-force attack.
{% endhint %}

First, we need to precisely define the "finding a password" problem. Let's assume we have a hash obtained from processing of an unknown password using the "phpass" algorithm.

{% hint style="info" %}
Phpass is used as a hashing method by e.g. WordPress and Drupal. Those are free/open-source web frameworks used to run PHP-based websites.
{% endhint %}

The password hash is stored in `in.hash` file and the hash is:

```
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/
```

We're going to assume that we know the password mask. It is:

```
?a?a?a
```

That means that the password consists of 3 alphanumeric characters.

Now we can try to find the password, matching the given hash and mask, by calling:

```
hashcat -a 3 -m 400 in.hash ?a?a?a
```

The parameters are:

* `a 3` - use a brute-force attack. There are 5 other types of attacks.
* `m 400` - password is hashed with the phpass algorithm. There are 320 other alghoritms supported by hashcat.
* `in.hash` - name of a file containing the hashed password
* `?a?a?a` - mask to use

{% hint style="info" %}
The complete hashcat arguments reference is available here: [https://hashcat.net/wiki/doku.php?id=hashcat](https://hashcat.net/wiki/doku.php?id=hashcat)
{% endhint %}

As a result of the above call, the `hashcat.potfile` will be created with the following content:

```
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/:pas
```

where `pas` is the password which had been unknown to us and was just retrieved by hashcat.

{% hint style="info" %}
Obviously, for longer passwords, the presented usage of hashcat could be problematic as it would require a lot more processing time (e.g. days or even months) to find a password with such a naive method.
{% endhint %}

To showcase how a similar problem can be resolved faster, we created the Golem version of hashcat. It uses the computing power of many providers at the same time. Parallelized password recovery can be much quicker - instead of days or months, this Golem version is likely to solve the problem in hours.

## Doings things in parallel

How to make hashcat work in parallel? The answer is quite simple: the keyspace concept. We can ask the tool to tell us what the size of the possibility space (keyspace) is for the given mask and algorithm:

```
hashcat --keyspace -a 3 ?a?a?a -m 400
```

As a result, we will receive an answer in the standard output. In our case it is `9025`.

Now we can divide the `0..9025` space into separate fragments. Assuming we want to allow our app to use up to 3 separate workers (which means up to 3 providers), those parts would be:

* `0..3008`
* `3009..6016`
* `6017..9025`

To process only the part of the whole `0..9025` space, we use the `--skip` and `--limit` options:

```
hashcat -a 3 -m 400 in.hash --skip 3009 --limit 6016  ?a?a?a
```

The above call will process the `3009..6016` part. If there is any result in that range it will be written to the `hashcat.potfile`.

## Before we begin

In order to develop applications for the Golem network, you need to install yagna daemon on your machine. We're going to assume you're already familiar with the setup of the environment required to run Python high-level API examples. If you're not, please make sure you proceed through our quick primer to get up to speed:

{% content-ref url="../flash-tutorial-of-requestor-development/" %}
[flash-tutorial-of-requestor-development](../flash-tutorial-of-requestor-development/)
{% endcontent-ref %}

Once you're done with the tutorial above, make sure you're again in yapapi's main directory and move to:

```
cd examples/yacat
```

{% hint style="success" %}
So now, we're going to assume that:

* The `yagna` deamon is running in the background.
* The `YAGNA_APPKEY` environment variable is set to the value of the generated app key.
* The payment is initialized with `yagna payment init -sender` (please keep in mind that it needs initialization after each launch of `yagna service run`).
* The virtual python environment for our tutorial is activated.
* Dependencies are installed and the `yajsapi` repository (containing the tutorial examples) is cloned.
* In your current directory (`examples/yacat`) there are two files that will be used and discussed in this example:
  * `yacat.Dockerfile` - the Docker file used for the definition of the provider's container images
  * `yacat.ts` - requestor agent's entry point which deals with orchestration of the container runs.
{% endhint %}

## Let's get to work - the Dockerfile

Let's start with the Dockerfile (`yacat.Dockerfile`). Do we always need a dedicated Dockerfile for our own Golem application?

{% hint style="info" %}
Golem is designed to use existing Docker images, so you can use any existing docker image. There are no Golem-specific conditions that need to be met by the image.
{% endhint %}

If there is (for example on the [docker hub](https://hub.docker.com/)) no docker image that you need, you will have to create a custom one.

For the yacat example we're going to use an off-the-shelf hashcat image (`dizcza/docker-hashcat:intel-cpu)` and just slightly modify it for Golem. Resultant Dockerfile is included in the example as `yacat.Dockerfile`:

```
FROM dizcza/docker-hashcat:intel-cpu

VOLUME /golem/input /golem/output
WORKDIR /golem/entrypoint
```

As Golem does not need any specific elements in the Dockerfile,`yacat.Dockerfile`is more or less a standard Dockerfile.

### VOLUME: the input/output

The one thing we need to remember while preparing the Dockerfile is to define a place (or places) in the container file system that will be used for the file transfer. We are going to use input (from requestor to the provider) and output (from provider to the requestor) file transfers here.

The volume is defined in the last line of the above Dockerfile:

```
VOLUME /golem/input /golem/output
```

This makes `/golem/input` and `/golem/output` locations we will use for our input/output file transfer. For the requestor agent code, which we are going to discuss in the next chapter, we need to know the volume (or volumes) name(s) and use it as a directory for the file transfers.

![](../../.gitbook/assets/requestor-vm-comms.jpg)

{% hint style="info" %}
On the provider side, all the content of the VOLUME directories is stored in the provider's os file system.

All the changes in other (non VOLUME mounted) container directories content are kept in RAM. The rest of the VM image file system (not changed, non VOLUME mounted) content is stored as VM image in the provider's os file system.
{% endhint %}

{% hint style="danger" %}
Please mind that tasks within a single worker instance - so effectively part of the same activity on a given provider node - run within the same virtual machine and share the contents of a VOLUME between each other.

That means that as long as the execution takes place on the same provider, and thus, on the same filesystem, files in the VOLUME left over from one task execution will be present in a subsequent run.
{% endhint %}

{% hint style="warning" %}
If your provider-side code creates large temporary files, you should store them in the directory defined as VOLUME. Otherwise, the large files will be stored in RAM. RAM usually has a capacity limit much lower than disk space.
{% endhint %}

### Important note about Docker's ENTRYPOINT

Because of how Golem's VM execution unit works, the Docker's usual `ENTRYPOINT` statement present in the Dockerfiles is effectively ignored and replaced with the exeunit's own entrypoint.

The net effect for you, the developer, is that - at least for the time being - you cannot rely on that feature in your Dockerfiles. Instead, you can pass the relevant commands from the requestor agent as part of the execution script after the image is deployed and started on provider's VM. This will be shown in the next step of this tutorial.

### Build process

Now we may proceed with a regular Docker build, using `yacat.Dockerfile`:

```python
docker build . -f yacat.Dockerfile -t yacat
```

As Golem cannot currently use raw docker images and uses its own, optimized `gvmkit` image format, we have to convert our Docker image the following way:

```python
pip install gvmkit-build
gvmkit-build yacat
gvmkit-build yacat --push
```

The important fact is that the last of the above commands, will provide us with a `gvmkit` image hash, that looks like this:

```python
2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9
```

{% hint style="info" %}
This hash will identify our image when our Golem application is run. Please copy and save it somewhere as in the requestor agent code, we will need to pass it to the `Engine` in order to have providers use the correct image for the container instances.
{% endhint %}

The details of docker image conversion are described here:

{% content-ref url="../vm-runtime/convert-a-docker-image-into-a-golem-image.md" %}
[convert-a-docker-image-into-a-golem-image.md](../vm-runtime/convert-a-docker-image-into-a-golem-image.md)
{% endcontent-ref %}

## The requestor agent code

Let's look at the core of our hashcat example - the requestor agent. Please check the `yacat.ts` file below.

{% hint style="info" %}
The critical fragments of `yacat.ts` will be described in the following sections of the tutorial so now, you can just do a quick scan over the big code block below.
{% endhint %}

```typescript
import { TaskExecutor } from "../../dist";
import { program } from "commander";
async function main(args) {
  const executor = await TaskExecutor.create({
    package: "055911c811e56da4d75ffc928361a78ed13077933ffa8320fb1ec2db",
    maxParallelTasks: args.numberOfProviders,
    budget: 10,
    subnetTag: args.subnetTag,
    payment: { driver: args.paymentDriver, network: args.paymentNetwork },
    logLevel: args.debug ? "debug" : "info",
  });
  const keyspace = await executor.run<number>(async (ctx) => {
    const result = await ctx.run(`hashcat --keyspace -a 3 ${args.mask} -m 400`);
    return parseInt(result.stdout || "");
  });

  if (!keyspace) throw new Error(`Cannot calculate keyspace`);
  console.log(`Keyspace size computed. Keyspace size = ${keyspace}.`);
  const step = Math.floor(keyspace / args.numberOfProviders + 1);
  const range = [...Array(Math.floor(keyspace / step)).keys()].map((i) => i + step);

  const results = executor.map(range, async (ctx, skip = 0) => {
    const results = await ctx
            .beginBatch()
            .run(`hashcat -a 3 -m 400 '${args.hash}' '${args.mask}' --skip=${skip} --limit=${skip + step} -o pass.potfile`)
            .run("cat pass.potfile")
            .end()
            .catch((err) => console.error(err));
    if (!results?.[1]?.stdout) return false;
    return results?.[1]?.stdout.split(":")[1];
  });

  let password = "";
  for await (const result of results) {
    if (result) {
      password = result;
      break;
    }
  }
  if (!password) console.log("No password found");
  else console.log(`Password found: ${password}`);
  await executor.end();
}

program
  .option("--subnet-tag <subnet>", "set subnet name, for example 'public'")
  .option("--payment-driver, --driver <driver>", "payment driver name, for example 'erc20'")
  .option("--payment-network, --network <network>", "network name, for example 'rinkeby'")
  .option("-d, --debug", "output extra debugging")
  .option("--number-of-providers <number_of_providers>", "number of providers", (value) => parseInt(value), 3)
  .option("--mask <mask>")
  .requiredOption("--hash <hash>");
program.parse();
const options = program.opts();
main(options).catch((e) => console.error(e));

```

## So what is happening here?

We start with a high-level overview of the steps performed by the requestor agent. In the [next section](hashcat.md#how-does-the-code-work) we'll dig into the implementation details.

### Compute keyspace size

The first step in the computation is to **check the keyspace size**. For this we only need to execute `hashcat` with `--keyspace`, as show in the section [Doing things in parallel](task-example-2-hashcat.md#doings-things-in-parallel) and read that command's output.

### Define the tasks

Knowing the keyspace size we define the list of **tasks** to execute on providers. Recall from the section [Doing things in parallel](task-example-2-hashcat.md#doings-things-in-parallel) that we can run `hashcat` on a fragment of the whole keyspace, using the `--skip` and `--limit` parameters. In this step for each such fragment we define a separate task.

Knowing the number of tasks we can also determine the number of providers required to execute them in parallel. In this example we decided that the number of providers contracted for the work will be equal to the number of tasks divided by two. This does not necessarily mean that every provider will get exactly two tasks, even if the overall number of tasks is even, because:

{% hint style="info" %}
When a provider is ready to execute a task, it takes up the next task from a common pool of tasks, so a fast provider may end up executing more tasks than a slow one.
{% endhint %}

### Perform mask attack

Next, we can start looking for the password using multiple **workers**, executing the tasks on multiple providers at the same time.

In order to look for passwords in the given keyspace range, for each of the workers employed to perform our job, we are executing the following steps:

* Execute`hashcat` with proper `--skip` and `--limit` values on the provider
* Get the `hashcat_{skip}.potfile` from the provider to the requestor
* Parse the result from the `.potfile`

![](<../../.gitbook/assets/tutorial-03 (1).jpg>)

## How does the code work?

### The argument parser

We use library `commander` to pass arguments such as `--mask` and `--max-workers`, and it will print a nice argument description and an example invocation when we run the requestor script with `--help`.

### The `main` function

Let's now jump to the `main` function which contains the main body of the requestor app. Its sole argument, `args`, contains information on the command-line arguments read by the argument parser.

```typescript
async function main(args) 
```

#### Task Executor and package definition

To run our tasks on the Golem network we need to create a `TaskExewcutor` instance.

```typescript
const executor = await TaskExecutor.create({
    package: "055911c811e56da4d75ffc928361a78ed13077933ffa8320fb1ec2db",
    minMemGib: 1,
    minStorageGib: 1,
    maxParallelTasks: args.numberOfProviders,
    budget: 10,
    subnetTag: args.subnetTag,
    payment: { driver: args.paymentDriver, network: args.paymentNetwork },
    logLevel: args.debug ? "debug" : "info",
  });
```
One of the required parameter is `packae` with which we pass the image hash. The image hash parameter points to the image that we want the containers to run - here we use the hash received from `gvmkit-build`.

The other arguments arguments are as follows:

* `minMemGib` defines minimum memory requirement for provider,
* `minStorageGib` defines minimum storage requirement for provider,
* `maxParallelTasks` specifies the maximum number of parallel task runs,
* `budget` defines maximal spendings for executing all the tasks with `Golem`,
* `subnetTag` specifies the providers subnet to be used; it's best to leave the default value in place unless you mean to run your own network of test providers to test the app against,
* `payment`:`driver` and `network` parameters that select the Ethereum blockchain and the payment driver for you; for example, you would not use the mainnet network for tests but you'll probably want to run the real-live tasks on the mainnet to be able to use all the providers that participate in the Golem network.
* `logLevel` defines levels for default logger.

#### First call to `executor.run`: Computing keyspace size

With `TaskExecutor` instance running we may proceed with sending tasks to providers. For this we use one of the execution method: `run`.

```typescript
  const keyspace = await executor.run<number>(async (ctx) => {
  const result = await ctx.run(`hashcat --keyspace -a 3 ${args.mask} -m 400`);
  return parseInt(result.stdout || "");
});
```

This call tells `TaskExecutor` to execute a single task defined by worker function `async (ctx) =>`. The `ctx` object allow us to run single (or batch) command in the provider side.
The keyspace size can be read from the `result` attribute of the executed command.

#### Second call to `executor.map`: Performing the attack

Now we can split the whole `keyspace` into chunks depend on maximum number of providers and prepare a `range` of computations for each task:

```typescript
  const step = Math.floor(keyspace / args.numberOfProviders + 1);
  const range = [...Array(Math.floor(keyspace / step)).keys()].map((i) => i + step);
```

With the `range` we call `executor.map` method to run splitted task simultaneously in golem network.

```typescript
const results = executor.map(range, async (ctx, skip = 0) => {
    const results = await ctx
      .beginBatch()
      .run(`hashcat -a 3 -m 400 '${args.hash}' '${args.mask}' --skip=${skip} --limit=${skip + step} -o pass.potfile`)
      .run("cat pass.potfile")
      .end()
      .catch((err) => console.error(err));
    if (!results?.[1]?.stdout) return false;
    return results?.[1]?.stdout.split(":")[1];
  });
```

The `results` object is type of `AsyncIterable` which we can iterate by `for await` statement:

```typescript
for await (const result of results) {
    if (result) {
      password = result;
      break;
    }
  }
```


## Example run

While in the `/examples/yacat` directory, type the following:

```sh
ts-node yacat.ts  --mask '?a?a?a' --hash '$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/'
```

{% hint style="danger" %}
Please note that to run .ts files directly you need to have installed 

* use `ts-node`
* or you can compile `.ts` by `tsc` and run `.js` file by standard nodejs interpreter

{% endhint %}

The above run should return "pas" as the recovered password.

`yacat.ts` supports a few optional parameters. To get help on those, please type:

```sh
ts-node yacat.ts --help
```

