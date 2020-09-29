# yapapi.runner

## Sub-modules

* [yapapi.runner.ctx](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/runner/ctx/README.md)
* [yapapi.runner.events](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/runner/events/README.md)
* [yapapi.runner.utils](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/runner/utils/README.md)
* [yapapi.runner.vm](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/runner/vm/README.md)

## Variables

```text
CFF_DEFAULT_PRICE_FOR_COUNTER
```

```text
CFG_INVOICE_TIMEOUT
```

```text
SCORE_NEUTRAL
```

```text
SCORE_REJECTED
```

```text
SCORE_TRUSTED
```

```text
TaskData
```

```text
TaskResult
```

## Classes

### DummyMS

```text
class DummyMS(
    max_for_counter: Mapping[yapapi.props.com.Counter, decimal.Decimal] = mappingproxy({<Counter.TIME: 'golem.usage.duration_sec'>: Decimal('0.002'), <Counter.CPU: 'golem.usage.cpu_sec'>: Decimal('0.020')}),
    max_fixed: decimal.Decimal = Decimal('0.05')
)
```

DummyMS\(max\_for\_counter: Mapping\[yapapi.props.com.Counter, decimal.Decimal\] = mappingproxy\({: Decimal\('0.002'\), : Decimal\('0.020'\)}\), max\_fixed: decimal.Decimal = Decimal\('0.05'\)\)

#### Ancestors \(in MRO\)

* yapapi.runner.MarketStrategy
* abc.ABC

#### Class variables

```text
max_fixed
```

```text
max_for_counter
```

#### Methods

#### decorate\_demand

```text
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

#### score\_offer

```text
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### Engine

```text
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

#### Ancestors \(in MRO\)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Methods

#### map

```text
def map(
    self,
    worker: Callable[[yapapi.runner.ctx.WorkContext, AsyncIterator[ForwardRef('Task')]], AsyncIterator[Tuple[ForwardRef('Task'), yapapi.runner.ctx.Work]]],
    data
)
```

Run computations on providers.

:param worker: a callable that takes a WorkContext object and a list o tasks, adds commands to the context object and yields committed commands :param data: an iterator of Task objects to be computed on providers :return: yields computation progress events

### LeastExpensiveLinearPayuMS

```text
class LeastExpensiveLinearPayuMS(
    expected_time_secs: int = 60
)
```

LeastExpensiveLinearPayuMS\(expected\_time\_secs: int = 60\)

#### Ancestors \(in MRO\)

* yapapi.runner.MarketStrategy
* abc.ABC

#### Methods

#### decorate\_demand

```text
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

#### score\_offer

```text
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### MarketStrategy

```text
class MarketStrategy(
    /,
    *args,
    **kwargs
)
```

Abstract market strategy

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.runner.DummyMS
* yapapi.runner.LeastExpensiveLinearPayuMS

#### Methods

#### decorate\_demand

```text
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
) -> None
```

#### score\_offer

```text
def score_offer(
    self,
    offer: yapapi.rest.market.OfferProposal
) -> float
```

### Package

```text
class Package(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.runner.vm.\_VmPackage

#### Methods

#### decorate\_demand

```text
def decorate_demand(
    self,
    demand: yapapi.props.builder.DemandBuilder
)
```

#### resolve\_url

```text
def resolve_url(
    self
) -> str
```

### Task

```text
class Task(
    data: ~TaskData,
    *,
    expires: Union[datetime.datetime, NoneType] = None,
    timeout: Union[datetime.timedelta, NoneType] = None
)
```

One computation unit.

Represents one computation unit that will be run on the provider \(e.g. rendering of one frame\).

#### Ancestors \(in MRO\)

* typing.Generic

#### Class variables

```text
ids
```

#### Instance variables

```text
data
```

```text
expires
```

```text
output
```

#### Methods

#### accept\_task

```text
def accept_task(
    self,
    result: Union[~TaskResult, NoneType] = None
)
```

Accept task that was completed.

Must be called when the results of a task are correct and it shouldn't be retried.

:param result: computation result \(optional\) :return: None

#### reject\_task

```text
def reject_task(
    self,
    reason: Union[str, NoneType] = None
)
```

Reject task.

Must be called when the results of the task are not correct and it should be retried.

:param reason: task rejection description \(optional\) :return: None

### TaskStatus

```text
class TaskStatus(
    /,
    *args,
    **kwargs
)
```

An enumeration.

#### Ancestors \(in MRO\)

* enum.Enum

#### Class variables

```text
ACCEPTED
```

```text
REJECTED
```

```text
RUNNING
```

```text
WAITING
```

```text
name
```

```text
value
```

