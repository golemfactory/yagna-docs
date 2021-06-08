# HL API: Work generator pattern and WorkContext

### Intro

Golem applications in general follow a pattern where a Requestor Agent application issue commands which are relayed to the Provider side and executed within the ExeUnit. The responses from the commands are fed back to the Requestor Agent application, and may be processed according to the application logic.

A high-level API library provides an abstraction over low-level Golem mechanics, and that includes Activity control, and the ExeScript commands. In all cases where ExeScript execution is required, this is instrumented using a _work generator pattern_.

Work generator pattern is a variation Command design pattern, where actions to be performed between Requestor Agent and the Provider's ExeUnit are represented by objects, which are marshalled by the high-level API library. Requestor Agent programmer is expected to develop code which generates the commands and returns them via an iterator/enumerator \(depending on the programming language\). Moreover, where possible, the work generator uses the `await/async` mechanics, to increase code execution efficiency.

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

A `worker()` function is specified, which will be called by high-level library engine, to iterate over the work commands and marshall the commands to the Provider. This function receives:

*  a `WorkContext` object, which is used to construct the commands
* a collection of `Task` objects which specify individualparts of the batch process to be executed.

Note how a `run()` method is called on the WorkContext instance to build a command to issue a `bash` statement on a remote VM. This call builds the RUN command and stores it in the `WorkContext`'s cache. 

A subsequent `commit()` call wraps all previously created commands in a batch, which is then returned \(via `yield` statement\) to the caller of the `worker()` method. The command cache is cleared and a new command batch can be started \(by further calls to `WorkContext` command construction API\).

The `yield` statement returns an awaitable object wrapping the command's results. This `future` object can be awaited to obtain the command's response, which can be processed further. The `worker()` execution halts until the generated work command gets processed.

{% hint style="info" %}
Note that some programming languages do not support receiving responses from a `yield` statement. In those languages the command results shall still be available via an awaitable object, available either from the command object itself, or from the `WorkContext`.
{% endhint %}

### WorkContext APIs

The `WorkContext` is a facade which exposes APIs to build various commands. Some useful methods are listed below:

#### `deploy()`

TBC

#### `start()`

TBC

#### `run(statement(, arguments))`

TBC

#### `send_*(location, <content>)`

TBC

#### `download_*(<content>, location)`

TBC



