Module yapapi.runner
====================

Sub-modules
-----------
* [yapapi.runner.ctx](ctx/)
* [yapapi.runner.events](events/)
* [yapapi.runner.utils](utils/)
* [yapapi.runner.vm](vm/)

Variables
---------

```python3
CFF_DEFAULT_PRICE_FOR_COUNTER
```

```python3
CFG_INVOICE_TIMEOUT
```

```python3
SCORE_NEUTRAL
```

```python3
SCORE_REJECTED
```

```python3
SCORE_TRUSTED
```

```python3
TaskData
```

```python3
TaskResult
```

Classes
-------

### DummyMS

```python3
class DummyMS(
    max_for_counter: Mapping[yapapi.props.com.Counter, decimal.Decimal] = mappingproxy({<Counter.TIME: 'golem.usage.duration_sec'>: Decimal('0.002'), <Counter.CPU: 'golem.usage.cpu_sec'>: Decimal('0.020')}),
    max_fixed: decimal.Decimal = Decimal('0.05')
)
```

DummyMS(max_for_counter: Mapping[yapapi.props.com.Counter, decimal.Decimal] = mappingproxy({<Counter.TIME: 'golem.usage.duration_sec'>: Decimal('0.002'), <Counter.CPU: 'golem.usage.cpu_sec'>: Decimal('0.020')}), max_fixed: decimal.Decimal = Decimal('0.05'))

#### Ancestors (in MRO)

* yapapi.runner.MarketStrategy
* abc.ABC

#### Class variables

```python3
max_fixed
```

```python3
max_for_counter
```

#### Methods

    
#### decorate_demand

```python3
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

    
#### score_offer

```python3
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### Engine

```python3
class Engine(
    *,
    package: 'Package',
    max_workers: int = 5,
    timeout: datetime.timedelta = datetime.timedelta(seconds=300),
    budget: Union[float, decimal.Decimal],
    strategy: yapapi.runner.MarketStrategy = DummyMS(max_for_counter=mappingproxy({<Counter.TIME: 'golem.usage.duration_sec'>: Decimal('0.002'), <Counter.CPU: 'golem.usage.cpu_sec'>: Decimal('0.020')}), max_fixed=Decimal('0.05')),
    subnet_tag: Union[str, NoneType] = None,
    event_emitter: yapapi.runner.events.EventEmitter[typing.Union[yapapi.runner.events.SubscriptionEvent, yapapi.runner.events.ProposalEvent, yapapi.runner.events.AgreementEvent, yapapi.runner.events.WorkerEvent, yapapi.runner.events.TaskEvent, yapapi.runner.events.StorageEvent]] = <function log_event at 0x10fcfae50>
)
```

Requestor engine. Used to run tasks based on a common package on providers.
    

#### Ancestors (in MRO)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Methods

    
#### map

```python3
def map(
    self,
    worker: Callable[[yapapi.runner.ctx.WorkContext, AsyncIterator[ForwardRef('Task')]], AsyncIterator[Tuple[ForwardRef('Task'), yapapi.runner.ctx.Work]]],
    data
)
```
Run computations on providers.

:param worker: a callable that takes a WorkContext object and a list o tasks,
               adds commands to the context object and yields committed commands
:param data: an iterator of Task objects to be computed on providers
:return: yields computation progress events

### LeastExpensiveLinearPayuMS

```python3
class LeastExpensiveLinearPayuMS(
    expected_time_secs: int = 60
)
```

LeastExpensiveLinearPayuMS(expected_time_secs: int = 60)

#### Ancestors (in MRO)

* yapapi.runner.MarketStrategy
* abc.ABC

#### Methods

    
#### decorate_demand

```python3
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

    
#### score_offer

```python3
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### MarketStrategy

```python3
class MarketStrategy(
    /,
    *args,
    **kwargs
)
```

Abstract market strategy

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.runner.DummyMS
* yapapi.runner.LeastExpensiveLinearPayuMS

#### Methods

    
#### decorate_demand

```python3
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

    
#### score_offer

```python3
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### Package

```python3
class Package(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.runner.vm._VmPackage

#### Methods

    
#### decorate_demand

```python3
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
)
```

    
#### resolve_url

```python3
def resolve_url(
    self
) -> str
```

### Task

```python3
class Task(
    data: ~TaskData,
    *,
    expires: Union[datetime.datetime, NoneType] = None,
    timeout: Union[datetime.timedelta, NoneType] = None
)
```

One computation unit.

Represents one computation unit that will be run on the provider
(e.g. rendering of one frame).

#### Ancestors (in MRO)

* typing.Generic

#### Class variables

```python3
ids
```

#### Instance variables

```python3
data
```

```python3
expires
```

```python3
output
```

#### Methods

    
#### accept_task

```python3
def accept_task(
    self,
    result: Union[~TaskResult, NoneType] = None
)
```
Accept task that was completed.

Must be called when the results of a task are correct and it shouldn't be retried.

:param result: computation result (optional)
:return: None

    
#### reject_task

```python3
def reject_task(
    self,
    reason: Union[str, NoneType] = None
)
```
Reject task.

Must be called when the results of the task
are not correct and it should be retried.

:param reason: task rejection description (optional)
:return: None

### TaskStatus

```python3
class TaskStatus(
    /,
    *args,
    **kwargs
)
```

An enumeration.

#### Ancestors (in MRO)

* enum.Enum

#### Class variables

```python3
ACCEPTED
```

```python3
REJECTED
```

```python3
RUNNING
```

```python3
WAITING
```

```python3
name
```

```python3
value
```