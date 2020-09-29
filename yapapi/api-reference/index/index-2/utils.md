# yapapi.runner.utils

Utility functions and classes used within the `yapapi.runner` package.

## Classes

### AsyncWrapper

```text
class AsyncWrapper(
    wrapped: Callable,
    event_loop: Union[asyncio.events.AbstractEventLoop, NoneType] = None
)
```

Wraps a given callable to provide asynchronous calls.

Example usage:

with AsyncWrapper\(func\) as wrapper: wrapper.async\_call\("Hello", world=True\) wrapper.async\_call\("Bye!"\)

The above code will make two asynchronous calls to `func`. The results of the calls, if any, are discarded, so this class is most useful for wrapping callables that return `None`.

#### Ancestors \(in MRO\)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Methods

#### async\_call

```text
def async_call(
    self,
    *args,
    **kwargs
) -> None
```

Schedule an asynchronous call to the wrapped callable.

