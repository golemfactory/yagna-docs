# yapapi.runner.events

Representing and logging events in Golem computation.

## Variables

```text
E
```

```text
EventType
```

```text
ResourceId
```

```text
logger
```

## Functions

#### log\_event

```text
def log_event(
    event_type: Union[yapapi.runner.events.SubscriptionEvent, yapapi.runner.events.ProposalEvent, yapapi.runner.events.AgreementEvent, yapapi.runner.events.WorkerEvent, yapapi.runner.events.TaskEvent, yapapi.runner.events.StorageEvent],
    resource_id: Union[int, str, NoneType] = None,
    **kwargs: Any
) -> None
```

Log an event. This function is compatible with the `EventEmitter` protocol.

## Classes

### AgreementEvent

```text
class AgreementEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to agreements.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
CONFIRMED
```

```text
CREATED
```

```text
INVOICE_RECEIVED
```

```text
PAYMENT_ACCEPTED
```

```text
PAYMENT_PREPARED
```

```text
PAYMENT_QUEUED
```

```text
REJECTED
```

```text
name
```

```text
value
```

### EventEmitter

```text
class EventEmitter(
    *args,
    **kwargs
)
```

A protocol for callables that can emit events of type `E`.

#### Ancestors \(in MRO\)

* typing.Protocol
* typing.Generic

### ProposalEvent

```text
class ProposalEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to proposals.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
BUFFERED
```

```text
FAILED
```

```text
RECEIVED
```

```text
REJECTED
```

```text
RESPONDED
```

```text
name
```

```text
value
```

### StorageEvent

```text
class StorageEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to storage.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
DOWNLOAD_FINISHED
```

```text
DOWNLOAD_STARTED
```

```text
name
```

```text
value
```

### SubscriptionEvent

```text
class SubscriptionEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to subscriptions.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
COLLECT_FAILED
```

```text
CREATED
```

```text
FAILED
```

```text
name
```

```text
value
```

### TaskEvent

```text
class TaskEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to tasks.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
ACCEPTED
```

```text
COMMAND_EXECUTED
```

```text
GETTING_RESULTS
```

```text
REJECTED
```

```text
SCRIPT_FINISHED
```

```text
SCRIPT_SENT
```

```text
name
```

```text
value
```

### WorkerEvent

```text
class WorkerEvent(
    /,
    *args,
    **kwargs
)
```

Types of events related to workers.

#### Ancestors \(in MRO\)

* yapapi.runner.events.\_EventStrMixin
* enum.Enum

#### Class variables

```text
ACTIVITY_CREATED
```

```text
ACTIVITY_CREATE_FAILED
```

```text
CREATED
```

```text
FINISHED
```

```text
GOT_TASK
```

```text
name
```

```text
value
```

