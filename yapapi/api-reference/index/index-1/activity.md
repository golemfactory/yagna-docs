# yapapi.rest.activity

## Classes

### Activity

```text
class Activity(
    _api: ya_activity.api.requestor_control_api.RequestorControlApi,
    _state: ya_activity.api.requestor_state_api.RequestorStateApi,
    activity_id: str
)
```

An abstract base class for asynchronous context managers.

#### Ancestors \(in MRO\)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Instance variables

```text
id
```

#### Methods

#### send

```text
def send(
    self,
    script: List[dict]
)
```

#### state

```text
def state(
    self
) -> ya_activity.models.activity_state.ActivityState
```

### ActivityService

```text
class ActivityService(
    api_client: ya_activity.api_client.ApiClient
)
```

#### Methods

#### new\_activity

```text
def new_activity(
    self,
    agreement_id: str
) -> 'Activity'
```

### Batch

```text
class Batch(
    _api: ya_activity.api.requestor_control_api.RequestorControlApi,
    activity_id: str,
    batch_id: str,
    batch_size: int
)
```

Abstract base class for generic types.

A generic type is typically declared by inheriting from this class parameterized with one or more type variables. For example, a generic mapping type might be defined as::

class Mapping\(Generic\[KT, VT\]\): def **getitem**\(self, key: KT\) -&gt; VT: ...

```text
  # Etc.
```

This class can then be used as follows::

def lookup\_name\(mapping: Mapping\[KT, VT\], key: KT, default: VT\) -&gt; VT: try: return mapping\[key\] except KeyError: return default

#### Ancestors \(in MRO\)

* collections.abc.AsyncIterable
* collections.abc.Sized
* typing.Generic

#### Instance variables

```text
id
```

### CommandExecutionError

```text
class CommandExecutionError(
    /,
    *args,
    **kwargs
)
```

Common base class for all non-exit exceptions.

#### Ancestors \(in MRO\)

* builtins.Exception
* builtins.BaseException

#### Class variables

```text
args
```

#### Methods

#### with\_traceback

```text
def with_traceback(
    ...
)
```

Exception.with_traceback\(tb\) -- set self.\_traceback_ to tb and return self.

### Result

```text
class Result(
    idx: int,
    message: Union[str, NoneType]
)
```

Result\(idx: int, message: Union\[str, NoneType\]\)

