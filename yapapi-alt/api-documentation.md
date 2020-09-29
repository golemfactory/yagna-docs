# API Reference

## yapapi

Golem Python API.

#### enable\_default\_logger

```python
enable_default_logger(format_: str = "[%(asctime)s %(levelname)s %(name)s] %(message)s", level: int = logging.INFO)
```

Enable the default logger that logs to stderr.

## yapapi.props

### Activity Objects

```python
@dataclass()
class Activity(Model)
```

Activity-related Properties

#### cost\_cap

Sets a Hard cap on total cost of the Activity \(regardless of the usage vector or pricing function\). The Provider is entitled to 'kill' an Activity which exceeds the capped cost amount indicated by Requestor.

#### cost\_warning

Sets a Soft cap on total cost of the Activity \(regardless of the usage vector or pricing function\). When the cost\_warning amount is reached for the Activity, the Provider is expected to send a Debit Note to the Requestor, indicating the current amount due

#### timeout\_secs

A timeout value for batch computation \(eg. used for container-based batch processes\). This property allows to set the timeout to be applied by the Provider when running a batch computation: the Requestor expects the Activity to take no longer than the specified timeout value - which implies that eg. the golem.usage.duration\_sec counter shall not exceed the specified timeout value.

## yapapi.props.builder

## yapapi.props.com

## yapapi.props.inf

Infrastructural Properties

## yapapi.props.base

## yapapi.runner

#### CFG\_INVOICE\_TIMEOUT

Time to receive invoice from provider after tasks ended.

### MarketStrategy Objects

```python
class MarketStrategy(abc.ABC)
```

Abstract market strategy

### Engine Objects

```python
class Engine(AsyncContextManager)
```

Requestor engine. Used to run tasks based on a common package on providers.

#### \_\_init\_\_

```python
 | __init__(*, package: "Package", max_workers: int = 5, timeout: timedelta = timedelta(minutes=5), budget: Union[float, Decimal], strategy: MarketStrategy = DummyMS(), subnet_tag: Optional[str] = None, event_emitter: EventEmitter[EventType] = log_event)
```

Create a new requestor engine.

**Arguments**:

* `package`: a package common for all tasks; vm.repo\(\) function may be

  used to return package from a repository

* `max_workers`: maximum number of workers doing the computation
* `timeout`: timeout for the whole computation
* `budget`: maximum budget for payments
* `strategy`: market strategy used to select providers from the market

  \(e.g. LeastExpensiveLinearPayuMS or DummyMS\)

* `subnet_tag`: use only providers in the subnet with the subnet\_tag name
* `event_emitter`: an EventEmitter that emits events related to the

  computation; by default it is a function that logs all events

#### map

```python
 | async map(worker: Callable[[WorkContext, AsyncIterator["Task"]], AsyncIterator[Tuple["Task", Work]]], data)
```

Run computations on providers.

**Arguments**:

* `worker`: a callable that takes a WorkContext object and a list o tasks,

  adds commands to the context object and yields committed commands

* `data`: an iterator of Task objects to be computed on providers

**Returns**:

yields computation progress events

### Task Objects

```python
class Task(Generic[TaskData, TaskResult],  object)
```

One computation unit.

Represents one computation unit that will be run on the provider \(e.g. rendering of one frame\).

#### \_\_init\_\_

```python
 | __init__(data: TaskData, *, expires: Optional[datetime] = None, timeout: Optional[timedelta] = None)
```

Create a new Task object.

**Arguments**:

* `data`: contains information needed to prepare command list for the provider
* `expires`: expiration datetime
* `timeout`: timeout from now; overrides expires parameter if provided

#### accept\_task

```python
 | accept_task(result: Optional[TaskResult] = None)
```

Accept task that was completed.

Must be called when the results of a task are correct and it shouldn't be retried.

**Arguments**:

* `result`: computation result \(optional\)

**Returns**:

None

#### reject\_task

```python
 | reject_task(reason: Optional[str] = None)
```

Reject task.

Must be called when the results of the task are not correct and it should be retried.

**Arguments**:

* `reason`: task rejection description \(optional\)

**Returns**:

None

## yapapi.runner.vm

#### repo

```python
async repo(*, image_hash: str, min_mem_gib: float = 0.5, min_storage_gib: float = 2.0) -> Package
```

Builds reference to application package.

* _image\_hash_: finds package by its contents hash.
* _min\_mem\_gib_: minimal memory required to execute application code.
* _min\_storage\_gib_ minimal disk storage to execute tasks.

## yapapi.runner.events

Representing and logging events in Golem computation.

### SubscriptionEvent Objects

```python
class SubscriptionEvent(_EventStrMixin,  Enum)
```

Types of events related to subscriptions.

### ProposalEvent Objects

```python
class ProposalEvent(_EventStrMixin,  Enum)
```

Types of events related to proposals.

### AgreementEvent Objects

```python
class AgreementEvent(_EventStrMixin,  Enum)
```

Types of events related to agreements.

### WorkerEvent Objects

```python
class WorkerEvent(_EventStrMixin,  Enum)
```

Types of events related to workers.

### TaskEvent Objects

```python
class TaskEvent(_EventStrMixin,  Enum)
```

Types of events related to tasks.

### StorageEvent Objects

```python
class StorageEvent(_EventStrMixin,  Enum)
```

Types of events related to storage.

### EventEmitter Objects

```python
class EventEmitter(Protocol[E])
```

A protocol for callables that can emit events of type `E`.

#### \_\_call\_\_

```python
 | __call__(event_type: E, resource_id: Optional[ResourceId] = None, **kwargs: Any) -> None
```

Emit an event with given event type and data.

#### log\_event

```python
log_event(event_type: EventType, resource_id: Optional[ResourceId] = None, **kwargs: Any, ,) -> None
```

Log an event. This function is compatible with the `EventEmitter` protocol.

## yapapi.runner.utils

Utility functions and classes used within the `yapapi.runner` package.

### AsyncWrapper Objects

```python
class AsyncWrapper(AsyncContextManager)
```

Wraps a given callable to provide asynchronous calls.

Example usage:

with AsyncWrapper\(func\) as wrapper: wrapper.async\_call\("Hello", world=True\) wrapper.async\_call\("Bye!"\)

The above code will make two asynchronous calls to `func`. The results of the calls, if any, are discarded, so this class is most useful for wrapping callables that return `None`.

#### async\_call

```python
 | async_call(*args, **kwargs) -> None
```

Schedule an asynchronous call to the wrapped callable.

## yapapi.runner.ctx

### WorkContext Objects

```python
class WorkContext()
```

An object used to schedule commands to be sent to provider.

#### send\_json

```python
 | send_json(json_path: str, data: dict)
```

Schedule sending JSON data to the provider.

**Arguments**:

* `json_path`: remote \(provider\) path
* `data`: dictionary representing JSON data

**Returns**:

None

#### send\_file

```python
 | send_file(src_path: str, dst_path: str)
```

Schedule sending file to the provider.

**Arguments**:

* `src_path`: local \(requestor\) path
* `dst_path`: remote \(provider\) path

**Returns**:

None

#### run

```python
 | run(cmd: str, *args: Iterable[str], *, env: Optional[Dict[str, str]] = None)
```

Schedule running a command.

**Arguments**:

* `cmd`: command to run on the provider, e.g. /my/dir/run.sh
* `args`: command arguments, e.g. "input1.txt", "output1.txt"
* `env`: optional dictionary with environmental variables

**Returns**:

None

#### download\_file

```python
 | download_file(src_path: str, dst_path: str)
```

Schedule downloading remote file from the provider.

**Arguments**:

* `src_path`: remote \(provider\) path
* `dst_path`: local \(requestor\) path

**Returns**:

None

#### commit

```python
 | commit(task: "Task") -> Tuple["Task", Work]
```

End task-related command list definition.

**Arguments**:

* `task`: task related to the list of commands

**Returns**:

a tuple of Task and Work objects \(the latter contains sequence commands added before calling this method\)

## yapapi.storage

Storage models.

### OutputStorageProvider Objects

```python
class OutputStorageProvider(abc.ABC)
```

#### new\_destination

```python
 | @abc.abstractmethod
 | async new_destination(destination_file: Optional[PathLike] = None) -> Destination
```

Creates slot for receiving file.

### Parameters

destination\_file: Optional hint where received data should be placed.

## yapapi.storage.webdav

## yapapi.storage.gftp

Golem File Transfer Storage Provider

### PubLink Objects

```python
class PubLink(TypedDict)
```

GFTP linking information.

#### file

file on local filesystem.

#### url

GFTP url as which local files is exposed.

### GftpDriver Objects

```python
class GftpDriver(Protocol)
```

Golem FTP service API.

#### version

```python
 | async version() -> str
```

Gets driver version.

#### publish

```python
 | async publish(*, files: List[str]) -> List[PubLink]
```

Exposes local file as GFTP url.

`files` : local files to be exposed

#### close

```python
 | async close(*, urls: List[str]) -> CommandStatus
```

Stops exposing GFTP urls created by [publish\(files=\[..\]\)](https://github.com/golemfactory/yagna-docs/tree/26a373962d43690ffd80a227553e8144eaa8fd96/yapapi2/%60publish%60/README.md).

#### receive

```python
 | async receive(*, output_file: str) -> PubLink
```

Creates GFTP url for receiving file.

: `output_file` -

#### shutdown

```python
 | async shutdown() -> CommandStatus
```

Stops GFTP service.

After shutdown all generated urls will be unavailable.

## yapapi.\_cli

## yapapi.\_cli.run

## yapapi.\_cli.market

### Demand Objects

```python
class Demand()
```

Offer subscription managment.

#### list

```python
 | @async_run
 | async list(only_expired: bool = False)
```

Lists all active demands

#### clear

```python
 | @async_run
 | async clear(only_expired: bool = False)
```

Removes demands.

By default removes all demands.

**Arguments**:

* `only_expired`: removes only expired demands.

## yapapi.\_cli.payment

### Allocation Objects

```python
class Allocation()
```

Payment allocation managment.

#### list

```python
 | @async_run
 | async list(details: bool = False)
```

Lists current active payment allocation

#### clear

```python
 | @async_run
 | async clear()
```

Removes all active payment allocations

### Invoices Objects

```python
class Invoices()
```

Invoice managment.

#### accept

```python
 | @async_run
 | async accept(allocation_id: str, invoice_id: str)
```

Accepts given `invoice_id` with `allocation_id`

**Arguments**:

* `allocation_id`: Allocation from which invoice will be paid. see

  `allocation list`.

* `invoice_id`: Invoice identifier.

#### list

```python
 | @async_run
 | async list(by_status: Optional[str] = None)
```

Lists all invoices.

## yapapi.\_\_main\_\_

## yapapi.rest

Mid level binding for Golem REST API

## yapapi.rest.configuration

## yapapi.rest.market

## yapapi.rest.activity

## yapapi.rest.resource

## yapapi.rest.payment

### Allocation Objects

```python
@dataclass
class Allocation(_Link)
```

Payment reservation for task processing.

#### id

Allocation object id

#### amount

Total amount allocated

#### expires

Allocation expiration timestamp

### Payment Objects

```python
class Payment(object)
```

#### new\_allocation

```python
 | new_allocation(amount: Decimal, *, expires: Optional[datetime] = None, make_deposit: bool = False) -> ResourceCtx[Allocation]
```

Creates new allocation.

* `amount`:  Allocation amount.
* `expires`: expiration timestamp. by default 30 minutes from now.
* `make_deposit`: \(unimplemented\).

#### allocations

```python
 | async allocations() -> AsyncIterator[Allocation]
```

Lists all active allocations.

**Example**:

Listing all active allocations

from yapapi import rest

async def list\_allocations\(payment\_api: rest.Payment\): async for allocation in payment\_api.allocations\(\):

* `print(f'''allocation` - {allocation.id}

  amount={allocation.amount},

  expires={allocation.expires}'''\)

