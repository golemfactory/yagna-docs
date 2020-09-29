<a name="yapapi"></a>
# yapapi

Golem Python API.

<a name="yapapi.enable_default_logger"></a>
#### enable\_default\_logger

```python
enable_default_logger(format_: str = "[%(asctime)s %(levelname)s %(name)s] %(message)s", level: int = logging.INFO)
```

Enable the default logger that logs to stderr.

<a name="yapapi.props"></a>
# yapapi.props

<a name="yapapi.props.Activity"></a>
## Activity Objects

```python
@dataclass()
class Activity(Model)
```

Activity-related Properties

<a name="yapapi.props.Activity.cost_cap"></a>
#### cost\_cap

Sets a Hard cap on total cost of the Activity (regardless of the usage vector or
pricing function). The Provider is entitled to 'kill' an Activity which exceeds the
capped cost amount indicated by Requestor.

<a name="yapapi.props.Activity.cost_warning"></a>
#### cost\_warning

Sets a Soft cap on total cost of the Activity (regardless of the usage vector or
pricing function). When the cost_warning amount is reached for the Activity,
the Provider is expected to send a Debit Note to the Requestor, indicating
the current amount due

<a name="yapapi.props.Activity.timeout_secs"></a>
#### timeout\_secs

A timeout value for batch computation (eg. used for container-based batch
processes). This property allows to set the timeout to be applied by the Provider
when running a batch computation: the Requestor expects the Activity to take
no longer than the specified timeout value - which implies that
eg. the golem.usage.duration_sec counter shall not exceed the specified
timeout value.

<a name="yapapi.props.builder"></a>
# yapapi.props.builder

<a name="yapapi.props.com"></a>
# yapapi.props.com

<a name="yapapi.props.inf"></a>
# yapapi.props.inf

Infrastructural Properties

<a name="yapapi.props.base"></a>
# yapapi.props.base

<a name="yapapi.runner"></a>
# yapapi.runner

<a name="yapapi.runner.CFG_INVOICE_TIMEOUT"></a>
#### CFG\_INVOICE\_TIMEOUT

Time to receive invoice from provider after tasks ended.

<a name="yapapi.runner.MarketStrategy"></a>
## MarketStrategy Objects

```python
class MarketStrategy(abc.ABC)
```

Abstract market strategy

<a name="yapapi.runner.Engine"></a>
## Engine Objects

```python
class Engine(AsyncContextManager)
```

Requestor engine. Used to run tasks based on a common package on providers.

<a name="yapapi.runner.Engine.__init__"></a>
#### \_\_init\_\_

```python
 | __init__(*, package: "Package", max_workers: int = 5, timeout: timedelta = timedelta(minutes=5), budget: Union[float, Decimal], strategy: MarketStrategy = DummyMS(), subnet_tag: Optional[str] = None, event_emitter: EventEmitter[EventType] = log_event)
```

Create a new requestor engine.

**Arguments**:

- `package`: a package common for all tasks; vm.repo() function may be
used to return package from a repository
- `max_workers`: maximum number of workers doing the computation
- `timeout`: timeout for the whole computation
- `budget`: maximum budget for payments
- `strategy`: market strategy used to select providers from the market
(e.g. LeastExpensiveLinearPayuMS or DummyMS)
- `subnet_tag`: use only providers in the subnet with the subnet_tag name
- `event_emitter`: an EventEmitter that emits events related to the
computation; by default it is a function that logs all events

<a name="yapapi.runner.Engine.map"></a>
#### map

```python
 | async map(worker: Callable[[WorkContext, AsyncIterator["Task"]], AsyncIterator[Tuple["Task", Work]]], data)
```

Run computations on providers.

**Arguments**:

- `worker`: a callable that takes a WorkContext object and a list o tasks,
adds commands to the context object and yields committed commands
- `data`: an iterator of Task objects to be computed on providers

**Returns**:

yields computation progress events

<a name="yapapi.runner.Task"></a>
## Task Objects

```python
class Task(Generic[TaskData, TaskResult],  object)
```

One computation unit.

Represents one computation unit that will be run on the provider
(e.g. rendering of one frame).

<a name="yapapi.runner.Task.__init__"></a>
#### \_\_init\_\_

```python
 | __init__(data: TaskData, *, expires: Optional[datetime] = None, timeout: Optional[timedelta] = None)
```

Create a new Task object.

**Arguments**:

- `data`: contains information needed to prepare command list for the provider
- `expires`: expiration datetime
- `timeout`: timeout from now; overrides expires parameter if provided

<a name="yapapi.runner.Task.accept_task"></a>
#### accept\_task

```python
 | accept_task(result: Optional[TaskResult] = None)
```

Accept task that was completed.

Must be called when the results of a task are correct and it shouldn't be retried.

**Arguments**:

- `result`: computation result (optional)

**Returns**:

None

<a name="yapapi.runner.Task.reject_task"></a>
#### reject\_task

```python
 | reject_task(reason: Optional[str] = None)
```

Reject task.

Must be called when the results of the task
are not correct and it should be retried.

**Arguments**:

- `reason`: task rejection description (optional)

**Returns**:

None

<a name="yapapi.runner.vm"></a>
# yapapi.runner.vm

<a name="yapapi.runner.vm.repo"></a>
#### repo

```python
async repo(*, image_hash: str, min_mem_gib: float = 0.5, min_storage_gib: float = 2.0) -> Package
```

Builds reference to application package.

- *image_hash*: finds package by its contents hash.
- *min_mem_gib*: minimal memory required to execute application code.
- *min_storage_gib* minimal disk storage to execute tasks.

<a name="yapapi.runner.events"></a>
# yapapi.runner.events

Representing and logging events in Golem computation.

<a name="yapapi.runner.events.SubscriptionEvent"></a>
## SubscriptionEvent Objects

```python
class SubscriptionEvent(_EventStrMixin,  Enum)
```

Types of events related to subscriptions.

<a name="yapapi.runner.events.ProposalEvent"></a>
## ProposalEvent Objects

```python
class ProposalEvent(_EventStrMixin,  Enum)
```

Types of events related to proposals.

<a name="yapapi.runner.events.AgreementEvent"></a>
## AgreementEvent Objects

```python
class AgreementEvent(_EventStrMixin,  Enum)
```

Types of events related to agreements.

<a name="yapapi.runner.events.WorkerEvent"></a>
## WorkerEvent Objects

```python
class WorkerEvent(_EventStrMixin,  Enum)
```

Types of events related to workers.

<a name="yapapi.runner.events.TaskEvent"></a>
## TaskEvent Objects

```python
class TaskEvent(_EventStrMixin,  Enum)
```

Types of events related to tasks.

<a name="yapapi.runner.events.StorageEvent"></a>
## StorageEvent Objects

```python
class StorageEvent(_EventStrMixin,  Enum)
```

Types of events related to storage.

<a name="yapapi.runner.events.EventEmitter"></a>
## EventEmitter Objects

```python
class EventEmitter(Protocol[E])
```

A protocol for callables that can emit events of type `E`.

<a name="yapapi.runner.events.EventEmitter.__call__"></a>
#### \_\_call\_\_

```python
 | __call__(event_type: E, resource_id: Optional[ResourceId] = None, **kwargs: Any) -> None
```

Emit an event with given event type and data.

<a name="yapapi.runner.events.log_event"></a>
#### log\_event

```python
log_event(event_type: EventType, resource_id: Optional[ResourceId] = None, **kwargs: Any, ,) -> None
```

Log an event. This function is compatible with the `EventEmitter` protocol.

<a name="yapapi.runner.utils"></a>
# yapapi.runner.utils

Utility functions and classes used within the `yapapi.runner` package.

<a name="yapapi.runner.utils.AsyncWrapper"></a>
## AsyncWrapper Objects

```python
class AsyncWrapper(AsyncContextManager)
```

Wraps a given callable to provide asynchronous calls.

Example usage:

  with AsyncWrapper(func) as wrapper:
      wrapper.async_call("Hello", world=True)
      wrapper.async_call("Bye!")

The above code will make two asynchronous calls to `func`.
The results of the calls, if any, are discarded, so this class is
most useful for wrapping callables that return `None`.

<a name="yapapi.runner.utils.AsyncWrapper.async_call"></a>
#### async\_call

```python
 | async_call(*args, **kwargs) -> None
```

Schedule an asynchronous call to the wrapped callable.

<a name="yapapi.runner.ctx"></a>
# yapapi.runner.ctx

<a name="yapapi.runner.ctx.WorkContext"></a>
## WorkContext Objects

```python
class WorkContext()
```

An object used to schedule commands to be sent to provider.

<a name="yapapi.runner.ctx.WorkContext.send_json"></a>
#### send\_json

```python
 | send_json(json_path: str, data: dict)
```

Schedule sending JSON data to the provider.

**Arguments**:

- `json_path`: remote (provider) path
- `data`: dictionary representing JSON data

**Returns**:

None

<a name="yapapi.runner.ctx.WorkContext.send_file"></a>
#### send\_file

```python
 | send_file(src_path: str, dst_path: str)
```

Schedule sending file to the provider.

**Arguments**:

- `src_path`: local (requestor) path
- `dst_path`: remote (provider) path

**Returns**:

None

<a name="yapapi.runner.ctx.WorkContext.run"></a>
#### run

```python
 | run(cmd: str, *args: Iterable[str], *, env: Optional[Dict[str, str]] = None)
```

Schedule running a command.

**Arguments**:

- `cmd`: command to run on the provider, e.g. /my/dir/run.sh
- `args`: command arguments, e.g. "input1.txt", "output1.txt"
- `env`: optional dictionary with environmental variables

**Returns**:

None

<a name="yapapi.runner.ctx.WorkContext.download_file"></a>
#### download\_file

```python
 | download_file(src_path: str, dst_path: str)
```

Schedule downloading remote file from the provider.

**Arguments**:

- `src_path`: remote (provider) path
- `dst_path`: local (requestor) path

**Returns**:

None

<a name="yapapi.runner.ctx.WorkContext.commit"></a>
#### commit

```python
 | commit(task: "Task") -> Tuple["Task", Work]
```

End task-related command list definition.

**Arguments**:

- `task`: task related to the list of commands

**Returns**:

a tuple of Task and Work objects (the latter contains
sequence commands added before calling this method)

<a name="yapapi.storage"></a>
# yapapi.storage

Storage models.

<a name="yapapi.storage.OutputStorageProvider"></a>
## OutputStorageProvider Objects

```python
class OutputStorageProvider(abc.ABC)
```

<a name="yapapi.storage.OutputStorageProvider.new_destination"></a>
#### new\_destination

```python
 | @abc.abstractmethod
 | async new_destination(destination_file: Optional[PathLike] = None) -> Destination
```

Creates slot for receiving file.

Parameters
----------
destination_file:
    Optional hint where received data should be placed.

<a name="yapapi.storage.webdav"></a>
# yapapi.storage.webdav

<a name="yapapi.storage.gftp"></a>
# yapapi.storage.gftp

Golem File Transfer Storage Provider

<a name="yapapi.storage.gftp.PubLink"></a>
## PubLink Objects

```python
class PubLink(TypedDict)
```

GFTP linking information.

<a name="yapapi.storage.gftp.PubLink.file"></a>
#### file

file on local filesystem.

<a name="yapapi.storage.gftp.PubLink.url"></a>
#### url

GFTP url as which local files is exposed.

<a name="yapapi.storage.gftp.GftpDriver"></a>
## GftpDriver Objects

```python
class GftpDriver(Protocol)
```

Golem FTP service API.

<a name="yapapi.storage.gftp.GftpDriver.version"></a>
#### version

```python
 | async version() -> str
```

Gets driver version.

<a name="yapapi.storage.gftp.GftpDriver.publish"></a>
#### publish

```python
 | async publish(*, files: List[str]) -> List[PubLink]
```

Exposes local file as GFTP url.

`files`
:   local files to be exposed

<a name="yapapi.storage.gftp.GftpDriver.close"></a>
#### close

```python
 | async close(*, urls: List[str]) -> CommandStatus
```

Stops exposing GFTP urls created by [publish(files=[..])](`publish`).

<a name="yapapi.storage.gftp.GftpDriver.receive"></a>
#### receive

```python
 | async receive(*, output_file: str) -> PubLink
```

Creates GFTP url for receiving file.

:  `output_file` -

<a name="yapapi.storage.gftp.GftpDriver.shutdown"></a>
#### shutdown

```python
 | async shutdown() -> CommandStatus
```

Stops GFTP service.

After shutdown all generated urls will be unavailable.

<a name="yapapi._cli"></a>
# yapapi.\_cli

<a name="yapapi._cli.run"></a>
# yapapi.\_cli.run

<a name="yapapi._cli.market"></a>
# yapapi.\_cli.market

<a name="yapapi._cli.market.Demand"></a>
## Demand Objects

```python
class Demand()
```

Offer subscription managment.

<a name="yapapi._cli.market.Demand.list"></a>
#### list

```python
 | @async_run
 | async list(only_expired: bool = False)
```

Lists all active demands

<a name="yapapi._cli.market.Demand.clear"></a>
#### clear

```python
 | @async_run
 | async clear(only_expired: bool = False)
```

Removes demands.

By default removes all demands.

**Arguments**:

- `only_expired`: removes only expired demands.

<a name="yapapi._cli.payment"></a>
# yapapi.\_cli.payment

<a name="yapapi._cli.payment.Allocation"></a>
## Allocation Objects

```python
class Allocation()
```

Payment allocation managment.

<a name="yapapi._cli.payment.Allocation.list"></a>
#### list

```python
 | @async_run
 | async list(details: bool = False)
```

Lists current active payment allocation

<a name="yapapi._cli.payment.Allocation.clear"></a>
#### clear

```python
 | @async_run
 | async clear()
```

Removes all active payment allocations

<a name="yapapi._cli.payment.Invoices"></a>
## Invoices Objects

```python
class Invoices()
```

Invoice managment.

<a name="yapapi._cli.payment.Invoices.accept"></a>
#### accept

```python
 | @async_run
 | async accept(allocation_id: str, invoice_id: str)
```

Accepts given `invoice_id` with `allocation_id`

**Arguments**:

- `allocation_id`: Allocation from which invoice will be paid. see
`allocation list`.
- `invoice_id`: Invoice identifier.

<a name="yapapi._cli.payment.Invoices.list"></a>
#### list

```python
 | @async_run
 | async list(by_status: Optional[str] = None)
```

Lists all invoices.

<a name="yapapi.__main__"></a>
# yapapi.\_\_main\_\_

<a name="yapapi.rest"></a>
# yapapi.rest

Mid level binding for Golem REST API

<a name="yapapi.rest.configuration"></a>
# yapapi.rest.configuration

<a name="yapapi.rest.market"></a>
# yapapi.rest.market

<a name="yapapi.rest.activity"></a>
# yapapi.rest.activity

<a name="yapapi.rest.resource"></a>
# yapapi.rest.resource

<a name="yapapi.rest.payment"></a>
# yapapi.rest.payment

<a name="yapapi.rest.payment.Allocation"></a>
## Allocation Objects

```python
@dataclass
class Allocation(_Link)
```

Payment reservation for task processing.

<a name="yapapi.rest.payment.Allocation.id"></a>
#### id

Allocation object id

<a name="yapapi.rest.payment.Allocation.amount"></a>
#### amount

Total amount allocated

<a name="yapapi.rest.payment.Allocation.expires"></a>
#### expires

Allocation expiration timestamp

<a name="yapapi.rest.payment.Payment"></a>
## Payment Objects

```python
class Payment(object)
```

<a name="yapapi.rest.payment.Payment.new_allocation"></a>
#### new\_allocation

```python
 | new_allocation(amount: Decimal, *, expires: Optional[datetime] = None, make_deposit: bool = False) -> ResourceCtx[Allocation]
```

Creates new allocation.

- `amount`:  Allocation amount.
- `expires`: expiration timestamp. by default 30 minutes from now.
- `make_deposit`: (unimplemented).

<a name="yapapi.rest.payment.Payment.allocations"></a>
#### allocations

```python
 | async allocations() -> AsyncIterator[Allocation]
```

Lists all active allocations.

**Example**:

  
  Listing all active allocations
  
  from yapapi import rest
  
  async def list_allocations(payment_api: rest.Payment):
  async for allocation in payment_api.allocations():
- `print(f'''allocation` - {allocation.id}
  amount={allocation.amount},
  expires={allocation.expires}''')

