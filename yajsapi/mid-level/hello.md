---
description: A minimal example of a functional Golem requestor agent
---

# Task Example 0: Hello World!

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* Mid-level components usage
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

```javascript
import {
  Package,
  Accounts,
  Allocation,
  Demand,
  DemandEvent,
  DemandEventType,
  Proposal,
  Agreement,
  Activity,
  Result,
  Deploy,
  Run,
  Script,
  Start,
} from "../../yajsapi/";
import { ConsoleLogger } from "../../yajsapi/utils";
async function main() {
  const logger = new ConsoleLogger();
  const vmPackage = await Package.create({ imageHash: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae" });
  const accounts = await (await Accounts.create({ yagnaOptions: { apiKey } })).list();
  const account = accounts.find((account) => account?.platform === 'erc20-rinkeby-tglm');
  if (!account) throw new Error("There is no available account");
  const allocation = await Allocation.create({ account, logger });
  const demand = await Demand.create(vmPackage, [allocation], { logger });
  const offer: Proposal = await new Promise((res) =>
    demand.addEventListener(DemandEventType, async (event) => {
      const proposalEvent = event as DemandEvent;
      if (proposalEvent.proposal.isInitial()) await proposalEvent.proposal.respond(account.platform);
      else if (proposalEvent.proposal.isDraft()) res(proposalEvent.proposal);
    })
  );
  const agreement = await Agreement.create(offer.id, { logger });
  await agreement.confirm();
  const activity = await Activity.create(agreement.id, { logger });
  const script = await Script.create([new Deploy(), new Start(), new Run("/bin/sh", ["-c", "echo 'Hello Golem'"])]);
  const exeScript = script.getExeScriptRequest();
  const streamResult = await activity.execute(exeScript);
  const results: Result[] = [];
  for await (const result of streamResult) results.push(result);
  console.log(results[2].stdout);
  await activity.stop();
  await agreement.terminate();
  await allocation.release();
  await demand.unsubscribe();
}
main().catch((e) => {
  console.error(e);
  process.exit(1);
});

```

## How does it work?

### The main() function

The interface of each module has mostly asynchronous methods, so we have to embed all the code inside the async function main.

### Logger
Each module has specific options. The constructor parameter that occurs in each of the modules is the `logger` object. It is responsible for showing messages during the lifetime of a given module. The logger object must implement the `Logger` (TODO: link to API reference) interface. In this example, we will use a ready-made `ConsoleLogger` implementation that prints all messages in the console.

```typescript
const logger = new ConsoleLogger();
```

### Package

The first component is `Package` (TODO: link to API reference). When creating a `Package`, we must determine which image we want to use. Currently, only VM images can be used, though with future implementations packages for wasm and other images will become feasible.

To create package we need defined `PackageOptions` (TODO: link to API reference):

```typescript
const vmPackage = await Package.create({ imageHash: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae" });
```

### Account

We need to know the account entity provided by yagna deamon. For list available account we can use:

```typescript
const accounts = await (await Accounts.create({ yagnaOptions: { apiKey } })).list();
```

and then find an account that has the appropriate payment platform:

```typescript
const account = accounts.find((account) => account?.platform === 'erc20-rinkeby-tglm');
```

For the purposes of this example, we choose an account that has the ability to make payments on the `erc20-rinkeby-tglm` platform.

### Allocation 

Now we need to create allocation for chosen account by: 

```typescript
const allocation = await Allocation.create({ account, logger });
```

An Allocation is a designated sum of money reserved for the purpose of making some particular payments. Allocations are currently purely virtual objects. An Allocation is connected to a payment account (wallet) specified by address and payment platform field.

### Demand

To create and publish `Demand` on the market, you need to create it for previously created package and allocation.

```typescript
const demand = await Demand.create(vmPackage, [allocation], { logger });
```

To customize the Demand object, you can pass the corresponding `DemandOptions` (TODO: link to API reference).

Demand object can be considered an "open" or public Demand, as it is not directed at a specific Provider, but rather is sent to the market so that the matching mechanism implementation can associate relevant Offers.
Note: it is an "atomic" operation, ie. as soon as Demand is created, the subscription is published on the market.

Demand is a special entity type because it inherits from the `EventTarget` class. Therefore, after creating it, you can add listeners to it, which will listen to offers from the market on an event of a specific type: `DemandEventType` (TODO: link to API reference), to do this, add a listener with:

```typescript
  const offer: Proposal = await new Promise((res) =>
    demand.addEventListener(DemandEventType, async (event) => {
      const proposalEvent = event as DemandEvent;
      if (proposalEvent.proposal.isInitial()) await proposalEvent.proposal.respond(account.platform);
      else if (proposalEvent.proposal.isDraft()) res(proposalEvent.proposal);
    })
  );
```

Each occurrence of the event checks whether it is the initial proposal from the provider (Proposal) or the next version - Draft (Offer).
If it is a proposal, we must respond to it using the `.respond(account.platform)` method and pass our payment platform as parameter.
In the case when it is a Draft, we can proceed to further process the offer.

### Agreement

Now we can create initial `Agreement` (TODO: link to API reference) with provider by:

```typescript
const agreement = await Agreement.create(offer.id, { logger });
```

This initiates the Agreement handshake phase. Created Agreement is in Proposal state. We can pass additional options `AgreementOptions` (TODO: link to API reference).

If the agreement is successfully created, we can accept it by:

```typescript
await agreement.confirm();
```

After that we have ability to create activity on provider side and run scripts.

### Activity

`Activity` (TODO: link to API reference) is an object representing the runtime environment on the provider in accordance with the `Package` specification.
As part of a given activity, it is possible to execute exe script commands and capture their results.

The first thing we need to do is create a script that consists of commands.

Depending on the type of runtime, the sent script should be in accordance with its specification.

In order to execute any `Run` command in VM Runtime, first we need to get our activity state to `Ready`. To do this, we need to send a script containing the `Deploy` and `Start` commands first,
then we can add any Run command.

```typescript
const script = await Script.create([
  new Deploy(),
  new Start(),
  new Run("/bin/sh", ["-c", "echo 'Hello World'"]),
]);
```

We can always check the status of our activity by:

```typescript
const state = await activity.getState();
```

After creating the script, we can execute it on our activity:

```typescript
const exeScript = script.getExeScriptRequest();
const streamResult = await activity.execute(exeScript);
```

As a result of executing the script, we receive a `Readable` object, which will asynchronously return the results of execution of individual commands. We can capture these results in two ways:

 - synchronously - using the `for await` construct: 
```typescript
  const results: Result[] = [];
  for await (const result of streamResult) results.push(result);
```
 - or asynchronously - by event handlers:
```typescript
streamResult.on("data", (result) => results.push(result));
streamResult.on("end", () => console.log("Execution done"));
```

Now in `results` we have an array of `Result` objects (TODO: link to API reference) indexed by command number in the script starting from 0.

To display the result of the Run command, do the following:

```typescript
console.log(results[2].stdout);
```

### Final tasks

After completing all tasks, you must end the activity and terminate the contract, release allocations and unsubscribe the demand. To do this, you must:

```typescript
await activity.stop();
await agreement.terminate();
await allocation.release();
await demand.unsubscribe();
```

And that's all.

{% hint style="warning" %}
In the current version, the payment acceptance mechanism has not yet been implemented.
{% endhint %}
