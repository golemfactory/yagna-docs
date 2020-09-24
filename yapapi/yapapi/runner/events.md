Module yapapi.runner.events
===========================
Representing and logging events in Golem computation.

Variables
---------

```python3
E
```

```python3
EventType
```

```python3
ResourceId
```

```python3
logger
```

Functions
---------

    
#### log_event

```python3
def log_event(
    event_type: Union[yapapi.runner.events.SubscriptionEvent, yapapi.runner.events.ProposalEvent, yapapi.runner.events.AgreementEvent, yapapi.runner.events.WorkerEvent, yapapi.runner.events.TaskEvent, yapapi.runner.events.StorageEvent],
    resource_id: Union[int, str, NoneType] = None,
    **kwargs: Any
) -> None
```
Log an event. This function is compatible with the `EventEmitter` protocol.

Classes
-------

### AgreementEvent

```python3
class AgreementEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to agreements.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
CONFIRMED
```

```python3
CREATED
```

```python3
INVOICE_RECEIVED
```

```python3
PAYMENT_ACCEPTED
```

```python3
PAYMENT_PREPARED
```

```python3
PAYMENT_QUEUED
```

```python3
REJECTED
```

```python3
name
```

```python3
value
```

### EventEmitter

```python3
class EventEmitter(
    *args,
    **kwargs
)
```

A protocol for callables that can emit events of type `E`.

#### Ancestors (in MRO)

* typing.Protocol
* typing.Generic

### ProposalEvent

```python3
class ProposalEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to proposals.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
BUFFERED
```

```python3
FAILED
```

```python3
RECEIVED
```

```python3
REJECTED
```

```python3
RESPONDED
```

```python3
name
```

```python3
value
```

### StorageEvent

```python3
class StorageEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to storage.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
DOWNLOAD_FINISHED
```

```python3
DOWNLOAD_STARTED
```

```python3
name
```

```python3
value
```

### SubscriptionEvent

```python3
class SubscriptionEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to subscriptions.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
COLLECT_FAILED
```

```python3
CREATED
```

```python3
FAILED
```

```python3
name
```

```python3
value
```

### TaskEvent

```python3
class TaskEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to tasks.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
ACCEPTED
```

```python3
COMMAND_EXECUTED
```

```python3
GETTING_RESULTS
```

```python3
REJECTED
```

```python3
SCRIPT_FINISHED
```

```python3
SCRIPT_SENT
```

```python3
name
```

```python3
value
```

### WorkerEvent

```python3
class WorkerEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to workers.

#### Ancestors (in MRO)

* yapapi.runner.events._EventStrMixin
* enum.Enum

#### Class variables

```python3
ACTIVITY_CREATED
```

```python3
ACTIVITY_CREATE_FAILED
```

```python3
CREATED
```

```python3
FINISHED
```

```python3
GOT_TASK
```

```python3
name
```

```python3
value
```