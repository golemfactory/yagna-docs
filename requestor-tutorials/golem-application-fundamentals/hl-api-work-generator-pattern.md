# HL API: Work generator pattern and WorkContext

### Intro

Golem applications in general follow a pattern where a Requestor Agent application issues commands which are relayed to the Provider side and executed within an execution unit. The responses from the commands are fed back to the Requestor Agent application, and may be processed according to the application logic.

A high-level API library provides an abstraction over low-level Golem mechanics, and that includes Activity control, and the ExeScript commands. In all cases where ExeScript execution is required, this is instrumented using a _work generator pattern_.

Work generator pattern is a variation of the Command design pattern, where actions to be performed between the Requestor agent and the Provider's execution unit are represented by objects, which are marshaled by the high-level API library. Requestor agent programmer is expected to develop code which generates the commands and returns them via an iterator/enumerator \(depending on the programming language\). Moreover, where possible, the work generator uses the `await/async` mechanics, to increase code execution efficiency.

### Basic example

Consider a simple code example of a work generator method/function/procedure:

{% tabs %}
{% tab title="Python" %}
```python
async def worker(context: WorkContext, tasks: AsyncIterable[Task]):
    async for task in tasks:
        context.run("/bin/sh", "-c", "date")

        future_results = yield context.commit()
        results = await future_results
        task.accept_result(result=results[-1])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
  async function* worker(context, tasks) {
    for await (let task of tasks) {
      context.run("/bin/sh", ["-c", "date"]);
      
      const future_result = yield context.commit();
      const { results } = await future_result;
      task.accept_result(results[results.length - 1])
    }
  }
```
{% endtab %}
{% endtabs %}

A `worker()` function is specified, which will be called by the high-level library engine for each provider, to iterate over the work commands and send the commands to the Provider. This function \(representing the task-based execution model\) receives:

*  a `WorkContext` object, which is used to construct the commands \(which is common to both the task-based API and the services' one\),
* a collection of `Task` objects which specify individual parts of the batch process to be executed \(specific to the task-based API\).

Note how a `run()` method is called on the WorkContext instance to build a command to issue a `bash` statement on a remote VM. This call builds a RUN command and appends to the `WorkContext`'s internal cache of pending commands. 

A subsequent `commit()` call wraps all previously created commands into a batch, which is then returned \(via `yield` statement\) to the caller of the `worker()` method. The command cache is cleared and a new command batch can be started \(by further calls to `WorkContext` command construction API\).

The `yield` statement returns an awaitable object wrapping the command's results. This `Future` object can be awaited upon to obtain the command's response, which can be processed further. The `worker()` execution for this specific provider halts until the generated work command gets processed.

{% hint style="info" %}
Note that some programming languages do not support receiving responses from a `yield` statement. In those languages the command results shall still be available via an awaitable object, available either from the command object itself, or from the `WorkContext`.
{% endhint %}

### WorkContext APIs

{% hint style="info" %}
**Note** that implementation of WorkContext APIs is specific to a ExeUnit/runtime which we communicate with. In other words, `run()` on a VM runtime means calling a shell command, while for a different runtime/ExeUnit it may have a different semantic, or may not be implemented at all.
{% endhint %}

The `WorkContext` is a facade which exposes APIs to build various commands. Some useful methods are listed below:

#### `run(statement(, arguments))`

TBC

#### `send_*(location, <content>)`

TBC

#### `download_*(<content>, location)`

TBC

#### `commit()`

TBC

...others...



