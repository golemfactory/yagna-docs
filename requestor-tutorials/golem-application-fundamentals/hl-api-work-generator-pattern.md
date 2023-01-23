# Work generator pattern and WorkContext

## Intro

Golem applications in general follow a pattern where a Requestor Agent application issues commands which are relayed to the Provider side and executed within an execution unit. The responses from the commands are fed back to the Requestor Agent application, and may be processed according to the application logic.

A high-level API library provides an abstraction over low-level Golem mechanics, and that includes Activity control, and the ExeScript commands. In all cases where ExeScript execution is required, this is instrumented using a _work generator pattern_.

Work generator pattern is a variation of the Command design pattern, where actions to be performed between the Requestor agent and the Provider's execution unit are represented by Script objects, which are marshaled by the high-level API library. Requestor agent programmer is expected to develop code which generates those scripts and returns them via an iterator/enumerator \(depending on the programming language\). Moreover, where possible, the work generator uses the `await/async` mechanics, to increase code execution efficiency.

## Basic example

Consider a simple code example of a work generator method/function/procedure:

{% tabs %}
{% tab title="Python" %}
```python
async def worker(context: WorkContext, tasks: AsyncIterable[Task]):
    async for task in tasks:
        script = context.new_script()
        future_result = script.run("/bin/sh", "-c", "date")
        yield script
        task.accept_result(result=await future_result)
```

A `worker()` function is specified, which will be called by the high-level library engine for each provider, to iterate over the work commands and send the commands to the Provider. This function \(representing the task-based execution model\) receives:

* a `WorkContext` object, which is used to construct the commands \(which is common to both the task-based API and the services' one\),
* a collection of `Task` objects which specify individual parts of the batch process to be executed \(specific to the task-based API\).

For each set of commands that we'd like to execute on the provider's end, the `new_script()` is called on the `WorkContext` instance to create a `Script` object to hold our execution script.

Then, a `run()` method is called on the `Script`/`WorkContext` instance to build a command to issue a `bash` statement on a remote VM. This call builds a RUN command. Note that we're saving a handle to its future result \(which is an async awaitable that will be filled with the actual result later\).

A subsequent `yield` statement then sends the prepared script to the caller of the `worker()` method, which effectively passes it for execution by the provider.

Both the aforementioned `run` command and the `yield` statement return awaitable objects wrapping the results. Those `Future` objects can be awaited upon to obtain the response for a specific command or for the whole script respectively, which can be processed further. The `worker()` execution for this specific provider halts until the generated work command gets processed.

{% hint style="info" %}
Note that some programming languages do not support receiving responses from a `yield` statement. In those languages the command results shall still be available via an awaitable object, available either from the command object itself, or from the `WorkContext`.
{% endhint %}

{% endtab %}

{% tab title="JavaScript" %}
```typescript
  async function worker(context: WorkContext, data?: string): Promise<string> {
    const result = await context.run(`echo "${data}"`);
    return result.stdout;
  }
```

A `worker()` function is specified, which will be called by the high-level library engine for each provider, to run command or batch of commands (script) on the Provider. This function \(representing the task-based execution model\) receives:

* a `WorkContext` object, which is used to construct the commands / script,
* an optional `data` which specify individual parts of the batch process to be executed.

Inside the worker function, we have `context` object which is instance of the `WorkContext` represents executable interface on the provider side.

Then, a `run()` method is called on the `WorkContext` instance to build a command to issue a `bash` statement on a remote VM. This call builds a RUN command. Note that this is a asynchronous call and it will be resolved as `Result` object of batch execution.

This `Promise<Result>` objects can be awaited upon to obtain the response for a specific command or for the whole script respectively, which can be processed further. The `worker()` execution for this specific provider halts until the generated work command gets processed.

{% endtab %}

{% endtab %}
{% endtabs %}

## Script API

{% hint style="info" %}
**Note** that implementation of the Script API is specific to a ExeUnit/runtime which we communicate with. In other words, `run()` on a VM runtime may have a different semantic than on other runtimes, and in some ExeUnits it may not even be implemented at all.
{% endhint %}

{% tabs %} {% tab title="Python" %}
The `Script` is a facade which exposes APIs to build various commands. Some useful methods are listed below:

### `run(statement(, arguments))`

Execute an arbitrary statement \(with arguments\) in the ExeUnit/runtime.

{% hint style="info" %}
The semantics of the command is specific to a runtime, eg. for VM runtime this command executes a shell statement and returns results from `stdout` and `stderr`.
{% endhint %}

### `send_*(location, <content>)`

A group of commands responsible for sending content to the ExeUnit. These are utility methods, which conveniently allow for sending eg. local files, binary content or JSON content.

### `download_*(<content>, location)`

A group of commands responsible for downloading content from the ExeUnit. As with `send_*()`, these are utility methods which allow for convenient transfer and conversion of remote content into local files, bytes or JSON objects.
{% endtab %}

{% tab title="JavaScript" %}

The `WorkContext` expose APIs to build various command or scripts. Some useful methods are listed below:

### ```async run(statement: string, ...arguments?: string[]): Promise<Result>```

Execute an arbitrary statement \(with arguments\) in the ExeUnit/runtime.

{% hint style="info" %}
The semantics of the command is specific to a runtime, eg. for VM runtime this command executes a shell statement and returns results from `stdout` and `stderr`.
{% endhint %}

### ```async upload(src: string, dst: string): Promise<Result>``

A group of commands responsible for sending content to the ExeUnit. These are utility methods, which conveniently allow for sending eg. local files, binary content or JSON content. 

### ```async download(src: string, dst: string): Promise<Result>```

A group of commands responsible for downloading content from the ExeUnit. As with `download()`, these are utility methods which allow for convenient transfer and conversion of remote content into local files, bytes or JSON objects.

{% hint style="info" %}
The `upload` and `download` command is available only in Nodejs environment. This is not supported in browser context in the current version.
{% endhint %}

{% endtab %}
{% endtabs %}
