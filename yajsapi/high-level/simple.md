---
description: A simple usage examples of Task Executor API 
---

# Task Example 1: Simple usage Task API

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* TaskExecutor create
* TaskExecutor run function
* TaskExecutor map function
* TaskExecutor forEach function
* TaskExecutor beforeEach function
* WorkContext API

{% endhint %}

## Creating an Executor instance

The executor can be created by passing appropriate initial parameters such as package, budget, subnet tag, payment driver, payment network etc.
One required parameter is a package. This can be done in two ways. First by passing only package image hash, e.g.
```js
const executor = await TaskExecutor.create("9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae"); 
```
Or by passing some optional parameters, e.g.
```js
const executor = await TaskExecutor.create({
  subnetTag: "public",
  payment: { driver: "erc-20", network: "rinkeby" },
  package: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
});
```

## Executing one of the available executor methods: `run`, `map` or `forEach`.

### `run` method

To execute single `worker` function on the golem (single provider) we need to use `run` method of executor API:

```js
  await executor.run(async (ctx) => console.log((await ctx.run("echo 'Hello World'")).stdout));
```

### `map` method

To get results for each element in iterable object, e.g.

```js
  const data = [1, 2, 3, 4, 5];
  const results = executor.map(data, (ctx, item) => providerCtx.ctx(`echo "${item}"`));
  for await (const result of results) console.log(result.stdout);
```

In the `results` variable, we have an async iterable object, with each element accessible with the `for await` statement.

### forEach` method

It is very similar to a map, but it does not return any value, e.g.

```js
  const data = [1, 2, 3, 4, 5];
  await executor.forEach(data, async (ctx, item) => {
      console.log((await ctx.run(`echo "${item}"`).stdout));
  });
```


## Worker Function and Work Context API

Each of the available methods: `run`, `map` and `forEach` takes the `worker` function as a parameter. The worker function is asynchronous and provides a `Work Context API` - `ctx` object.

Work Context allows running single commands or batches of commands on a provider.

Single commands available to run on a provider:

- `run()`
- `uploadFile()`
- `uploadJson()`
- `downloadFile()`

You can also compose particular commands into batches. For this, you should use `beginBatch`, e.g.

```js
const res = await ctx
   .beginBatch()
   .run('echo "Hello Golem"')
   .run('echo "Hello World"')
   .uploadJson({ hello: 'Golem'}, '/golem.json')
   .end()
   .catch((error) => console.error(error));

res?.map(({ stdout }) => console.log(stdout));
```
You can end the batch of commands by using the `end()` method shown above, meaning this code returns a `Promise` of multiple `Result` objects (or throw an error if occurred).

You can also end this batch by `endStream()` to get a `Readable` stream, e.g.

```js
const results = await ctx
   .beginBatch()
   .run('echo "Hello Golem"')
   .run('echo "Hello World"')
   .uploadJson({ hello: 'Golem'}, '/golem.json')
   .endStream();

 results.on("data", ({ stdout }) => console.log(stdout));
 results.on("error", (error) => console.error(error));
 results.on("close", () => console.log("END"));
```

### Additional executor method `beforeEach()`

There is a special method available in the executor object, that allows you to run the worker function once before each worker executes other tasks on the provider, but within the same activity. This is `beforeEach()` method.
This method takes as a parameter one worker function and runs it only once for each new provider activity. The following example demonstrates the use of this method.

```js
  executor.beforeEach(async (ctx) => {
    await ctx.uploadFile("./params.txt", "/params.txt");
  });

  await executor.forEach([1, 2, 3, 4, 5], async (ctx, item) => {
     await ctx
       .beginBatch()
       .run(`/run_some_command.sh --input ${item}--params /input_params.txt --output /output.txt`)
       .downloadFile("/output.txt", "./output.txt")
       .end();
  });
```
