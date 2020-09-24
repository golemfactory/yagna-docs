Module yapapi.rest.activity
===========================

Classes
-------

### Activity

```python3
class Activity(
    _api: ya_activity.api.requestor_control_api.RequestorControlApi,
    _state: ya_activity.api.requestor_state_api.RequestorStateApi,
    activity_id: str
)
```

An abstract base class for asynchronous context managers.

#### Ancestors (in MRO)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Instance variables

```python3
id
```

#### Methods

    
#### send

```python3
def send(
    self,
    script: List[dict]
)
```

    
#### state

```python3
def state(
    self
) -> ya_activity.models.activity_state.ActivityState
```

### ActivityService

```python3
class ActivityService(
    api_client: ya_activity.api_client.ApiClient
)
```

#### Methods

    
#### new_activity

```python3
def new_activity(
    self,
    agreement_id: str
) -> 'Activity'
```

### Batch

```python3
class Batch(
    _api: ya_activity.api.requestor_control_api.RequestorControlApi,
    activity_id: str,
    batch_id: str,
    batch_size: int
)
```

Abstract base class for generic types.

A generic type is typically declared by inheriting from
this class parameterized with one or more type variables.
For example, a generic mapping type might be defined as::

  class Mapping(Generic[KT, VT]):
      def __getitem__(self, key: KT) -> VT:
          ...
      # Etc.

This class can then be used as follows::

  def lookup_name(mapping: Mapping[KT, VT], key: KT, default: VT) -> VT:
      try:
          return mapping[key]
      except KeyError:
          return default

#### Ancestors (in MRO)

* collections.abc.AsyncIterable
* collections.abc.Sized
* typing.Generic

#### Instance variables

```python3
id
```

### CommandExecutionError

```python3
class CommandExecutionError(
    /,
    *args,
    **kwargs
)
```

Common base class for all non-exit exceptions.

#### Ancestors (in MRO)

* builtins.Exception
* builtins.BaseException

#### Class variables

```python3
args
```

#### Methods

    
#### with_traceback

```python3
def with_traceback(
    ...
)
```
Exception.with_traceback(tb) --
set self.__traceback__ to tb and return self.

### Result

```python3
class Result(
    idx: int,
    message: Union[str, NoneType]
)
```

Result(idx: int, message: Union[str, NoneType])