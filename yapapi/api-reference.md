# API Reference

## yapapi

Golem Python API.

#### get\_version

```python
get_version() -> str
```

**Returns**:

the version of the yapapi library package

#### windows\_event\_loop\_fix

```python
windows_event_loop_fix()
```

Set up asyncio to use ProactorEventLoop implementation for new event loops on Windows.

This work-around is only needed for Python 3.6 and 3.7. With Python 3.8, `ProactorEventLoop` is already the default on Windows.

## yapapi.strategy

Implementation of strategies for choosing offers from market.

### ComputationHistory Objects

```python
class ComputationHistory(Protocol)
```

A protocol for objects that provide information about the history of current computation.

#### rejected\_last\_agreement

```python
 | rejected_last_agreement(issuer_id) -> bool
```

Return True iff the previous agreement proposed to `issuer_id` has been rejected.

### MarketStrategy Objects

```python
class MarketStrategy(DemandDecorator,  abc.ABC)
```

Abstract market strategy.

#### decorate\_demand

```python
 | async decorate_demand(demand: DemandBuilder) -> None
```

Optionally add relevant constraints to a Demand.

#### score\_offer

```python
 | async score_offer(offer: rest.market.OfferProposal, history: Optional[ComputationHistory] = None) -> float
```

Score `offer`. Better offers should get higher scores.

### DummyMS Objects

```python
@dataclass
class DummyMS(MarketStrategy,  object)
```

A default market strategy implementation.

Its `score_offer()` method returns `SCORE_NEUTRAL` for every offer with prices that do not exceed maximum prices specified for each counter. For other offers, returns `SCORE_REJECTED`.

#### decorate\_demand

```python
 | async decorate_demand(demand: DemandBuilder) -> None
```

Ensure that the offer uses `PriceModel.LINEAR` price model.

#### score\_offer

```python
 | async score_offer(offer: rest.market.OfferProposal, history: Optional[ComputationHistory] = None) -> float
```

Score `offer`. Returns either `SCORE_REJECTED` or `SCORE_NEUTRAL`.

### LeastExpensiveLinearPayuMS Objects

```python
@dataclass
class LeastExpensiveLinearPayuMS(MarketStrategy,  object)
```

A strategy that scores offers according to cost for given computation time.

#### decorate\_demand

```python
 | async decorate_demand(demand: DemandBuilder) -> None
```

Ensure that the offer uses `PriceModel.LINEAR` price model.

#### score\_offer

```python
 | async score_offer(offer: rest.market.OfferProposal, history: Optional[ComputationHistory] = None) -> float
```

Score `offer` according to cost for expected computation time.

### DecreaseScoreForUnconfirmedAgreement Objects

```python
class DecreaseScoreForUnconfirmedAgreement(MarketStrategy)
```

A market strategy that modifies a base strategy based on history of agreements.

#### \_\_init\_\_

```python
 | __init__(base_strategy, factor)
```

**Arguments**:

* `base_strategy`: the base strategy around which this strategy is wrapped
* `factor`: the factor by which the score of an offer for a provider which

  failed to confirm the last agreement proposed to them will be multiplied

#### decorate\_demand

```python
 | async decorate_demand(demand: DemandBuilder) -> None
```

Decorate `demand` using the base strategy.

#### score\_offer

```python
 | async score_offer(offer: rest.market.OfferProposal, history: Optional[ComputationHistory] = None) -> float
```

Score `offer` using the base strategy and apply penalty if needed.

If the offer issuer failed to approve the previous agreement \(if any\) then the base score is multiplied by `self._factor`.

## yapapi.ctx

### Work Objects

```python
class Work(abc.ABC)
```

#### prepare

```python
 | async prepare()
```

A hook to be executed on requestor's end before the script is sent to the provider.

#### register

```python
 | register(commands: CommandContainer)
```

A hook which adds the required command to the exescript.

#### post

```python
 | async post()
```

A hook to be executed on requestor's end after the script has finished.

#### timeout

```python
 | @property
 | timeout() -> Optional[timedelta]
```

Return the optional timeout set for execution of this work.

### Steps Objects

```python
class Steps(Work)
```

#### \_\_init\_\_

```python
 | __init__(*steps: Work, *, timeout: Optional[timedelta] = None)
```

Create a `Work` item consisting of a sequence of steps \(subitems\).

**Arguments**:

* `steps`: sequence of steps to be executed
* `timeout`: timeout for waiting for the steps' results

#### timeout

```python
 | @property
 | timeout() -> Optional[timedelta]
```

Return the optional timeout set for execution of all steps.

#### prepare

```python
 | async prepare()
```

Execute the `prepare` hook for all the defined steps.

#### register

```python
 | register(commands: CommandContainer)
```

Execute the `register` hook for all the defined steps.

#### post

```python
 | async post()
```

Execute the `post` step for all the defined steps.

### ExecOptions Objects

```python
@dataclass
class ExecOptions()
```

Options related to command batch execution.

### WorkContext Objects

```python
class WorkContext()
```

An object used to schedule commands to be sent to provider.

#### id

Unique identifier for this work context.

#### provider\_name

```python
 | @property
 | provider_name() -> Optional[str]
```

Return the name of the provider associated with this work context.

#### deploy

```python
 | deploy()
```

Schedule a Deploy command.

#### start

```python
 | start(*args: str)
```

Schedule a Start command.

#### terminate

```python
 | terminate()
```

Schedule a Terminate command.

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

#### send\_bytes

```python
 | send_bytes(dst_path: str, data: bytes)
```

Schedule sending bytes data to the provider.

**Arguments**:

* `dst_path`: remote \(provider\) path
* `data`: bytes to send

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

#### download\_bytes

```python
 | download_bytes(src_path: str, on_download: Callable[[bytes], Awaitable], limit: int = DOWNLOAD_BYTES_LIMIT_DEFAULT)
```

Schedule downloading a remote file as bytes

**Arguments**:

* `src_path`: remote \(provider\) path
* `on_download`: the callable to run on the received data
* `limit`: the maximum length of the expected byte string

  :return None

#### download\_json

```python
 | download_json(src_path: str, on_download: Callable[[Any], Awaitable], limit: int = DOWNLOAD_BYTES_LIMIT_DEFAULT)
```

Schedule downloading a remote file as JSON

**Arguments**:

* `src_path`: remote \(provider\) path
* `on_download`: the callable to run on the received JSON data
* `limit`: the maximum length of the expected remote file

  :return None

#### commit

```python
 | commit(timeout: Optional[timedelta] = None) -> Work
```

Creates a sequence of commands to be sent to provider.

**Returns**:

Work object containing the sequence of commands scheduled within this work context before calling this method\)

## yapapi.executor

An implementation of the new Golem's task executor.

#### CFG\_INVOICE\_TIMEOUT

Time to receive invoice from provider after tasks ended.

#### DEFAULT\_EXECUTOR\_TIMEOUT

Joint timeout for all tasks submitted to an executor.

### Executor Objects

```python
class Executor(AsyncContextManager)
```

Task executor.

Used to run batch tasks using the specified application package within providers' execution units.

#### \_\_init\_\_

```python
 | @overload
 | __init__(*, payload: Optional[Payload] = None, max_workers: int = 5, timeout: timedelta = DEFAULT_EXECUTOR_TIMEOUT, _engine: _Engine)
```

Initialize the `Executor` to use a specific Golem `_engine`.

#### \_\_init\_\_

```python
 | @overload
 | __init__(*, budget: Union[float, Decimal], strategy: Optional[MarketStrategy] = None, subnet_tag: Optional[str] = None, driver: Optional[str] = None, network: Optional[str] = None, event_consumer: Optional[Callable[[Event], None]] = None, stream_output: bool = False, payload: Optional[Payload] = None, max_workers: int = 5, timeout: timedelta = DEFAULT_EXECUTOR_TIMEOUT)
```

Initialize the `Executor` for standalone usage, with `payload` parameter.

#### \_\_init\_\_

```python
 | @overload
 | __init__(*, budget: Union[float, Decimal], strategy: Optional[MarketStrategy] = None, subnet_tag: Optional[str] = None, driver: Optional[str] = None, network: Optional[str] = None, event_consumer: Optional[Callable[[Event], None]] = None, stream_output: bool = False, max_workers: int = 5, timeout: timedelta = DEFAULT_EXECUTOR_TIMEOUT, package: Optional[Payload] = None)
```

Initialize the `Executor` for standalone usage, with `package` parameter.

#### \_\_init\_\_

```python
 | __init__(*, budget: Optional[Union[float, Decimal]] = None, strategy: Optional[MarketStrategy] = None, subnet_tag: Optional[str] = None, driver: Optional[str] = None, network: Optional[str] = None, event_consumer: Optional[Callable[[Event], None]] = None, stream_output: bool = False, max_workers: int = 5, timeout: timedelta = DEFAULT_EXECUTOR_TIMEOUT, package: Optional[Payload] = None, payload: Optional[Payload] = None, _engine: Optional[_Engine] = None)
```

Initialize an `Executor`.

**Arguments**:

* `budget`: \[DEPRECATED use `Golem` instead\] maximum budget for payments
* `strategy`: \[DEPRECATED use `Golem` instead\] market strategy used to

  select providers from the market \(e.g. LeastExpensiveLinearPayuMS or DummyMS\)

* `subnet_tag`: \[DEPRECATED use `Golem` instead\] use only providers in the

  subnet with the subnet\_tag name

* `driver`: \[DEPRECATED use `Golem` instead\] name of the payment driver

  to use or `None` to use the default driver;

  only payment platforms with the specified driver will be used

* `network`: \[DEPRECATED use `Golem` instead\] name of the network

  to use or `None` to use the default network;

  only payment platforms with the specified network will be used

* `event_consumer`: \[DEPRECATED use `Golem` instead\] a callable that

  processes events related to the computation;

  by default it is a function that logs all events

* `stream_output`: \[DEPRECATED use `Golem` instead\]

  stream computation output from providers

* `max_workers`: maximum number of concurrent workers performing the computation
* `payload`: specification of payload \(for example a VM package\) that needs to be

  deployed on providers in order to compute tasks with this Executor

* `timeout`: timeout for the whole computation

#### driver

```python
 | @property
 | driver() -> str
```

Return the payment driver used for this `Executor`'s engine.

#### network

```python
 | @property
 | network() -> str
```

Return the payment network used for this `Executor`'s engine.

#### \_\_aenter\_\_

```python
 | async __aenter__() -> "Executor"
```

Start computation using this `Executor`.

#### \_\_aexit\_\_

```python
 | async __aexit__(exc_type, exc_val, exc_tb)
```

Release resources used by this `Executor`.

#### emit

```python
 | emit(event: events.Event) -> None
```

Emit a computation event using this `Executor`'s engine.

#### submit

```python
 | async submit(worker: Callable[
 |             [WorkContext, AsyncIterator[Task[D, R]]],
 |             AsyncGenerator[WorkItem, Awaitable[List[events.CommandEvent]]],
 |         ], data: Union[AsyncIterator[Task[D, R]], Iterable[Task[D, R]]]) -> AsyncIterator[Task[D, R]]
```

Submit a computation to be executed on providers.

**Arguments**:

* `worker`: a callable that takes a WorkContext object and a list o tasks,

  adds commands to the context object and yields committed commands

* `data`: an iterable or an async generator iterator of Task objects to be computed

  on providers

**Returns**:

yields computation progress events

## yapapi.executor.strategy

## yapapi.executor.ctx

## yapapi.executor.\_smartq

YAPAPI internal module. This is not a part of the public API. It can change at any time.

### Handle Objects

```python
class Handle(Generic[Item])
```

Handle of the queue item, iow, binding between a queue item and a specific consumer.

Additionally it keeps track of the previously used consumers of the given item to prevent them from being assigned to this item again.

### SmartQueue Objects

```python
class SmartQueue(Generic[Item])
```

#### \_\_init\_\_

```python
 | __init__(items: AsyncIterator[Item])
```

**Arguments**:

* `items`: the items to be iterated over

#### has\_unassigned\_items

```python
 | has_unassigned_items() -> bool
```

Check if this queue has a new or rescheduled item immediately available.

#### get

```python
 | async get(consumer: "Consumer[Item]") -> Handle[Item]
```

Get a handle to the next item to be processed \(either a new one or rescheduled\).

#### mark\_done

```python
 | async mark_done(handle: Handle[Item]) -> None
```

Mark an item, referred to by `handle`, as done.

#### reschedule

```python
 | async reschedule(handle: Handle[Item]) -> None
```

Free the item for reassignment to another consumer.

#### reschedule\_all

```python
 | async reschedule_all(consumer: "Consumer[Item]")
```

Make all items currently assigned to the consumer available for reassignment.

#### wait\_until\_done

```python
 | async wait_until_done() -> None
```

Wait until all items in the queue are processed.

### Consumer Objects

```python
class Consumer(
    Generic[Item], 
    AsyncIterator[Handle[Item]], 
    AsyncIterable[Handle[Item]], 
    ContextManager["Consumer[Item]"])
```

Provides an interface to asynchronously iterate over items in the given queue while cooperating with other consumers attached to this queue.

#### current\_item

```python
 | @property
 | current_item() -> Optional[Item]
```

The most-recent queue item that has been fetched to be processed by this consumer.

## yapapi.executor.task

### Task Objects

```python
class Task(Generic[TaskData, TaskResult])
```

One computation unit.

Represents one computation unit that will be run on the provider \(e.g. rendering of one frame of an animation\).

#### \_\_init\_\_

```python
 | __init__(data: TaskData)
```

Create a new Task object.

**Arguments**:

* `data`: contains information needed to prepare command list for the provider

#### running\_time

```python
 | @property
 | running_time() -> Optional[timedelta]
```

Return the running time of the task \(if in progress\) or time it took to complete it.

#### accept\_result

```python
 | accept_result(result: Optional[TaskResult] = None) -> None
```

Accept the result of this task.

Must be called when the result is correct to mark this task as completed.

**Arguments**:

* `result`: task computation result \(optional\)

**Returns**:

None

#### reject\_result

```python
 | reject_result(reason: Optional[str] = None, retry: bool = False) -> None
```

Reject the result of this task.

Must be called when the result is not correct to indicate that the task should be retried.

**Arguments**:

* `reason`: task rejection description \(optional\)

**Returns**:

None

## yapapi.executor.events

## yapapi.log

Utilities for logging computation events via the standard `logging` module.

Functions in this module fall into two categories:

* Functions that convert computation events generated by the `Executor.submit` method to calls to the standard Python `logging` module, using the loggers in the "yapapi" namespace \(e.g. `logging.getLogger("yapapi.executor")`\). These functions should be passed as `event_consumer` arguments to `Executor()`.
* Functions that perform configuration of the `logging` module itself. Since logging configuration is in general a responsibility of the code that uses `yapapi` as a library, we only provide the `enable_default_logger` function in this category, that enables logging to stderr with level `logging.INFO` and, optionally, to a given file with level `logging.DEBUG`.

### Functions for handling events

Several functions from this module can be passed as `event_consumer` callback to `yapapi.Executor()`.

For detailed, human-readable output use the `log_event` function:

```python
    Executor(..., event_consumer=yapapi.log.log_event)
```

For even more detailed, machine-readable output use `log_event_repr`:

```python
    Executor(..., event_consumer=yapapi.log.log_event_repr)
```

For summarized, human-readable output use `log_summary()`:

```python
    Executor(..., event_consumer=yapapi.log.log_summary())
```

Summary output can be combined with a detailed one by passing the detailed logger as an argument to `log_summary`:

```python
    Executor(
        ...
        event_consumer=yapapi.log.log_summary(yapapi.log.log_event_repr)
    )
```

#### enable\_default\_logger

```python
enable_default_logger(format_: str = "[%(asctime)s %(levelname)s %(name)s] %(message)s", log_file: Optional[str] = None, debug_activity_api: bool = False, debug_market_api: bool = False, debug_payment_api: bool = False)
```

Enable the default logger that logs messages to stderr with level `INFO`.

If `log_file` is specified, the logger with output messages with level `DEBUG` to the given file.

#### log\_event

```python
log_event(event: events.Event) -> None
```

Log `event` with a human-readable description.

#### log\_event\_repr

```python
log_event_repr(event: events.Event) -> None
```

Log the result of calling `repr(event)`.

### SummaryLogger Objects

```python
class SummaryLogger()
```

Aggregates information from computation events to provide a high-level summary.

The logger's `log()` method can be used as `event_consumer` callback to `Executor()`. It will aggregate the events generated by `Executor.submit()` and output some summary information.

The optional `wrapped_emitter` argument can be used for chaining event emitters: each event logged with `log()` is first passed to `wrapped_emitter`.

For example, with the following setup, each event emitted by `executor` will be logged by `log_event_repr`, and additionally, certain events will cause summary messages to be logged.

```python
    detailed_logger = log_event_repr
    summary_logger = SummaryLogger(wrapped_emitter=detailed_logger).log
    executor = Executor(..., event_consumer=summary_logger)
```

#### \_\_init\_\_

```python
 | __init__(wrapped_emitter: Optional[Callable[[events.Event], None]] = None)
```

Create a SummaryLogger.

#### log

```python
 | log(event: events.Event) -> None
```

Register an event.

#### log\_summary

```python
log_summary(wrapped_emitter: Optional[Callable[[events.Event], None]] = None)
```

Output a summary of computation.

This is a utility function that creates a `SummaryLogger` instance wrapping an optional `wrapped_emitter` and returns its `log` method.

See the documentation of `SummaryLogger` for more information.

#### pluralize

```python
pluralize(num: int, thing: str) -> str
```

Return the string f"1 {thing}" or f"{num} {thing}s", depending on `num`.

#### str\_capped

```python
str_capped(object: Any, max_len: int) -> str
```

Return the string representation of `object` trimmed to `max_len`.

Trailing ellipsis is added to the returned string if the original had to be trimmed.

## yapapi.rest

Mid-level binding for Golem REST API.

Serves as a more convenient interface between the agent code and the REST API.

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

#### payment\_platform

Payment platform, e.g. NGNT

#### payment\_address

Payment address, e.g. 0x123...

#### expires

Allocation expiration timestamp

### Payment Objects

```python
class Payment(object)
```

#### new\_allocation

```python
 | new_allocation(amount: Decimal, payment_platform: str, payment_address: str, *, expires: Optional[datetime] = None, make_deposit: bool = False) -> ResourceCtx[Allocation]
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

## yapapi.rest.configuration

### Configuration Objects

```python
class Configuration(object)
```

REST API's setup and top-level access utility.

By default, it expects the yagna daemon to be available locally and listening on the default port. The urls for the specific APIs are then based on this default base URL.

It requires one external argument, namely Yagna's application key, which is used to authenticate with the daemon. The application key must be either specified explicitly using the `app_key` argument or provided by the `YAGNA_APPKEY` environment variable.

If `YAGNA_API_URL` environment variable exists, it will be used as a base URL for all REST API URLs. Example value: [http://127.0.10.10:7500](http://127.0.10.10:7500) \(no trailing slash\).

Other than that, the URLs of each specific REST API can be overridden using the following environment variables:

* `YAGNA_MARKET_URL`
* `YAGNA_PAYMENT_URL`
* `YAGNA_ACTIVITY_URL`

#### app\_key

```python
 | @property
 | app_key() -> str
```

Yagna daemon's application key used to access the REST API.

#### market\_url

```python
 | @property
 | market_url() -> str
```

The URL of the Market REST API

#### payment\_url

```python
 | @property
 | payment_url() -> str
```

The URL of the Payment REST API

#### activity\_url

```python
 | @property
 | activity_url() -> str
```

The URL of the Activity REST API

#### market

```python
 | market() -> ya_market.ApiClient
```

Return a REST client for the Market API.

#### payment

```python
 | payment() -> ya_payment.ApiClient
```

Return a REST client for the Payment API.

#### activity

```python
 | activity() -> ya_activity.ApiClient
```

Return a REST client for the Activity API.

## yapapi.rest.resource

## yapapi.rest.activity

### ActivityService Objects

```python
class ActivityService(object)
```

A convenience helper to facilitate the creation of an Activity.

#### new\_activity

```python
 | async new_activity(agreement_id: str, stream_events: bool = False) -> "Activity"
```

Create an activity within bounds of the specified agreement.

**Returns**:

the object that represents the Activity and allows to query and control its state :rtype: Activity

### Activity Objects

```python
class Activity(AsyncContextManager["Activity"])
```

Mid-level wrapper for REST's Activity endpoint

#### state

```python
 | async state() -> yaa.ActivityState
```

Query the state of the activity.

#### send

```python
 | async send(script: List[dict], deadline: Optional[datetime] = None) -> "Batch"
```

Send the execution script to the provider's execution unit.

#### \_\_aexit\_\_

```python
 | async __aexit__(exc_type, exc_val, exc_tb) -> None
```

Call DestroyActivity API operation.

### CommandExecutionError Objects

```python
class CommandExecutionError(Exception)
```

An exception that indicates that a command failed on a provider.

#### command

The command that failed.

#### message

Optional error message from exe unit.

#### stderr

Stderr produced by the command running on provider.

### BatchTimeoutError Objects

```python
class BatchTimeoutError(Exception)
```

An exception that indicates that an execution of a batch of commands timed out.

### Batch Objects

```python
class Batch(abc.ABC,  AsyncIterable[events.CommandEventContext])
```

Abstract base class for iterating over events related to a batch running on provider.

#### seconds\_left

```python
 | seconds_left() -> float
```

Return how many seconds are left until the deadline.

#### id

```python
 | @property
 | id()
```

Return the ID of this batch.

### PollingBatch Objects

```python
class PollingBatch(Batch)
```

A `Batch` implementation that polls the server repeatedly for command status.

### StreamingBatch Objects

```python
class StreamingBatch(Batch)
```

A `Batch` implementation that uses event streaming to return command status.

## yapapi.rest.market

### AgreementDetails Objects

```python
class AgreementDetails(object)
```

### View Objects

```python
@dataclass
class View()
```

A certain fragment of an agreement's properties.

#### extract

```python
 | extract(m: Type[_ModelType]) -> _ModelType
```

Extract properties for the given model from this view's properties.

#### provider\_view

```python
 | @property
 | provider_view() -> View
```

Get the view of provider's properties in this Agreement.

#### requestor\_view

```python
 | @property
 | requestor_view() -> View
```

Get the view of requestor's properties in this Agreement.

### Agreement Objects

```python
class Agreement(object)
```

Mid-level interface to the REST's Agreement model.

#### confirm

```python
 | async confirm() -> bool
```

Sign and send the agreement to the provider and then wait for it to be approved.

**Returns**:

True if the agreement has been confirmed, False otherwise

#### terminate

```python
 | async terminate(reason: dict) -> bool
```

Terminate the agreement.

**Returns**:

True is the agreement has been successfully terminated, False otherwise.

### OfferProposal Objects

```python
class OfferProposal(object)
```

Mid-level interface to handle the negotiation phase between the parties.

#### reject

```python
 | async reject(reason: str = "Rejected")
```

Reject the Offer.

#### respond

```python
 | async respond(props: dict, constraints: str) -> str
```

Create an agreeement Proposal for a received Offer, based on our Demand.

#### create\_agreement

```python
 | async create_agreement(timeout=timedelta(hours=1)) -> Agreement
```

Create an Agreement based on this Proposal.

### Subscription Objects

```python
class Subscription(object)
```

Mid-level interface to REST API's Subscription model.

#### details

```python
 | @property
 | details() -> models.Demand
```

**Returns**:

the Demand for which the Subscription has been registered.

#### delete

```python
 | async delete()
```

Unsubscribe this Demand from the market.

#### events

```python
 | async events() -> AsyncIterator[OfferProposal]
```

Yield counter-proposals based on the incoming, matching Offers.

### Market Objects

```python
class Market(object)
```

Mid-level interface to the Market REST API.

#### subscribe

```python
 | subscribe(props: dict, constraints: str) -> AsyncResource[Subscription]
```

Create a subscription for a demand specified by the supplied properties and constraints.

#### subscriptions

```python
 | async subscriptions() -> AsyncIterator[Subscription]
```

Yield all the subscriptions that this requestor agent has on the market.

## yapapi.\_cli

## yapapi.\_cli.payment

### Allocation Objects

```python
class Allocation()
```

Payment allocation management.

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

Invoice management.

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

## yapapi.\_cli.run

## yapapi.\_cli.market

### Demand Objects

```python
class Demand()
```

Offer subscription management.

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

## yapapi.engine

#### DEBIT\_NOTE\_MIN\_TIMEOUT

Shortest debit note acceptance timeout the requestor will accept.

### NoPaymentAccountError Objects

```python
class NoPaymentAccountError(Exception)
```

The error raised if no payment account for the required driver/network is available.

#### required\_driver

Payment driver required for the account.

#### required\_network

Network required for the account.

#### \_\_init\_\_

```python
 | __init__(required_driver: str, required_network: str)
```

Initialize `NoPaymentAccountError`.

**Arguments**:

* `required_driver`: payment driver for which initialization was required
* `required_network`: payment network for which initialization was required

#### WorkItem

The type of items yielded by a generator created by the `worker` function supplied by user.

#### exescript\_ids

An iterator providing unique ids used to correlate events related to a single exe script.

### \_Engine Objects

```python
class _Engine(AsyncContextManager)
```

Base execution engine containing functions common to all modes of operation.

#### \_\_init\_\_

```python
 | __init__(*, budget: Union[float, Decimal], strategy: Optional[MarketStrategy] = None, subnet_tag: Optional[str] = None, driver: Optional[str] = None, network: Optional[str] = None, event_consumer: Optional[Callable[[events.Event], None]] = None, stream_output: bool = False, app_key: Optional[str] = None)
```

Initialize the engine.

**Arguments**:

* `budget`: maximum budget for payments
* `strategy`: market strategy used to select providers from the market

  \(e.g. LeastExpensiveLinearPayuMS or DummyMS\)

* `subnet_tag`: use only providers in the subnet with the subnet\_tag name
* `driver`: name of the payment driver to use or `None` to use the default driver;

  only payment platforms with the specified driver will be used

* `network`: name of the network to use or `None` to use the default network;

  only payment platforms with the specified network will be used

* `event_consumer`: a callable that processes events related to the

  computation; by default it is a function that logs all events

* `stream_output`: stream computation output from providers
* `app_key`: optional Yagna application key. If not provided, the default is to

  get the value from `YAGNA_APPKEY` environment variable

#### create\_demand\_builder

```python
 | async create_demand_builder(expiration_time: datetime, payload: Payload) -> DemandBuilder
```

Create a `DemandBuilder` for given `payload` and `expiration_time`.

#### driver

```python
 | @property
 | driver() -> str
```

Return the name of the payment driver used by this engine.

#### network

```python
 | @property
 | network() -> str
```

Return the name of the payment network used by this engine.

#### storage\_manager

```python
 | @property
 | storage_manager()
```

Return the storage manager used by this engine.

#### strategy

```python
 | @property
 | strategy() -> MarketStrategy
```

Return the instance of `MarketStrategy` used by this engine.

#### emit

```python
 | emit(event: events.Event) -> None
```

Emit an event to be consumed by this engine's event consumer.

#### \_\_aenter\_\_

```python
 | async __aenter__() -> "_Engine"
```

Initialize resources and start background services used by this engine.

#### accept\_payments\_for\_agreement

```python
 | async accept_payments_for_agreement(agreement_id: str, *, partial: bool = False) -> None
```

Add given agreement to the set of agreements for which invoices should be accepted.

#### accept\_debit\_notes\_for\_agreement

```python
 | accept_debit_notes_for_agreement(agreement_id: str) -> None
```

Add given agreement to the set of agreements for which debit notes should be accepted.

#### add\_job

```python
 | add_job(job: "Job")
```

Register a job with this engine.

#### finalize\_job

```python
 | @staticmethod
 | finalize_job(job: "Job")
```

Mark a job as finished.

### PaymentDecorator Objects

```python
@dataclass
class PaymentDecorator(DemandDecorator)
```

A `DemandDecorator` that adds payment-related constraints and properties to a Demand.

#### decorate\_demand

```python
 | async decorate_demand(demand: DemandBuilder)
```

Add properties and constraints to a Demand.

#### create\_activity

```python
 | async create_activity(agreement_id: str)
```

Create an activity for given `agreement_id`.

#### process\_batches

```python
 | async process_batches(agreement_id: str, activity: rest.activity.Activity, command_generator: AsyncGenerator[WorkItem, Awaitable[List[events.CommandEvent]]]) -> None
```

Send command batches produced by `command_generator` to `activity`.

### Job Objects

```python
class Job()
```

Functionality related to a single job.

Responsible for posting a Demand to market and collecting Offer proposals for the Demand.

#### \_\_init\_\_

```python
 | __init__(engine: _Engine, expiration_time: datetime, payload: Payload)
```

Initialize a `Job` instance.

param engine: a `Golem` engine which will run this job param expiration\_time: expiration time for the job; all agreements created for this job must expire before this date param payload: definition of a service runtime or a runtime package that needs to be deployed on providers for executing this job

#### find\_offers

```python
 | async find_offers() -> None
```

Create demand subscription and process offers.

When the subscription expires, create a new one. And so on...

## yapapi.\_\_main\_\_

## yapapi.package

## yapapi.package.vm

#### repo

```python
@deprecated(version="0.6.0", reason="moved to yapapi.payload.vm.repo")
async repo(*, image_hash: str, min_mem_gib: float = 0.5, min_storage_gib: float = 2.0) -> Package
```

Build reference to application package.

* _image\_hash_: finds package by its contents hash.
* _min\_mem\_gib_: minimal memory required to execute application code.
* _min\_storage\_gib_ minimal disk storage to execute tasks.

#### resolve\_repo\_srv

```python
@deprecated(version="0.6.0", reason="moved to yapapi.payload.vm.resolve_repo_srv")
resolve_repo_srv(repo_srv, fallback_url=_FALLBACK_REPO_URL) -> str
```

Get the url of the package repository based on its SRV record address.

**Arguments**:

* `repo_srv`: the SRV domain name
* `fallback_url`: temporary hardcoded fallback url in case there's a problem resolving SRV

**Returns**:

the url of the package repository containing the port :raises: PackageException if no valid service could be reached

## yapapi.golem

### Golem Objects

```python
class Golem(_Engine)
```

The main entrypoint of Golem's high-level API.

Provides two methods that reflect the two modes of operation, or two types of jobs that can currently be executed on the Golem network.

The first one - `execute_tasks` - instructs `Golem` to take a sequence of tasks that the user wishes to compute on Golem and distributes those among the providers.

The second one - `run_service` - instructs `Golem` to spawn a certain number of instances of a service based on a single service specification \(a specialized implementation inheriting from `yapapi.Service`\).

While the two models are not necessarily completely disjoint - in that we can create a service that exists to process a certain number of computations and, similarly, we can use the task model to run some service - the main difference lies in the lifetime of such a job.

Whereas a task-based job exists for the purpose of computing the specific sequence of tasks and is done once the whole sequence has been processed, the service-based job is created for a potentially indefinite period and the services spawned within it are kept alive for as long as they're needed.

Additionally, the service interface provides a way to easily define handlers for certain, discrete phases of a lifetime of each service instance - startup, running and shutdown.

As `Golem`'s job includes tracking and executing payments for activities spawned by either mode of operation, it's usually good to have just one instance of `Golem` active at any given time.

#### execute\_tasks

```python
 | async execute_tasks(worker: Callable[
 |             [WorkContext, AsyncIterator[Task[D, R]]],
 |             AsyncGenerator[WorkItem, Awaitable[List[events.CommandEvent]]],
 |         ], data: Union[AsyncIterator[Task[D, R]], Iterable[Task[D, R]]], payload: Payload, max_workers: Optional[int] = None, timeout: Optional[timedelta] = None, budget: Optional[Union[float, Decimal]] = None) -> AsyncIterator[Task[D, R]]
```

Submit a sequence of tasks to be executed on providers.

Internally, this method creates an instance of `yapapi.executor.Executor` and calls its `submit()` method with given worker function and sequence of tasks.

**Arguments**:

* `worker`: an async generator that takes a `WorkContext` object and a sequence

  of tasks, and generates as sequence of work items to be executed on providers in order

  to compute given tasks

* `data`: an iterable or an async generator of `Task` objects to be computed on providers
* `payload`: specification of the payload that needs to be deployed on providers

  \(for example, a VM runtime package\) in order to compute the tasks, passed to

  the created `Executor` instance

* `max_workers`: maximum number of concurrent workers, passed to the `Executor` instance
* `timeout`: timeout for computing all tasks, passed to the `Executor` instance
* `budget`: budget for computing all tasks, passed to the `Executor` instance

**Returns**:

an iterator that yields completed `Task` objects

example usage:

```python
async def worker(context: WorkContext, tasks: AsyncIterable[Task]):
    async for task in tasks:
    context.run("/bin/sh", "-c", "date")

    future_results = yield context.commit()
    results = await future_results
    task.accept_result(result=results[-1])

    package = await vm.repo(
        image_hash="d646d7b93083d817846c2ae5c62c72ca0507782385a2e29291a3d376",
    )

    async with Golem(budget=1.0, subnet_tag="devnet-beta.2") as golem:
        async for completed in golem.execute_tasks(worker, [Task(data=None)], payload=package):
            print(completed.result.stdout)
```

#### run\_service

```python
 | async run_service(service_class: Type[Service], num_instances: int = 1, payload: Optional[Payload] = None, expiration: Optional[datetime] = None) -> Cluster
```

Run a number of instances of a service represented by a given `Service` subclass.

**Arguments**:

* `service_class`: a subclass of `Service` that represents the service to be run
* `num_instances`: optional number of service instances to run, defaults to a single

  instance

* `payload`: optional runtime definition for the service; if not provided, the

  payload specified by the `get_payload()` method of `service_class` is used

* `expiration`: optional expiration datetime for the service

**Returns**:

a `Cluster` of service instances

example usage:

```python
DATE_OUTPUT_PATH = "/golem/work/date.txt"
REFRESH_INTERVAL_SEC = 5


class DateService(Service):
    @staticmethod
    async def get_payload():
        return await vm.repo(
            image_hash="d646d7b93083d817846c2ae5c62c72ca0507782385a2e29291a3d376",
        )

    async def start(self):
        # every `DATE_POLL_INTERVAL` write output of `date` to `DATE_OUTPUT_PATH`
        self._ctx.run(
            "/bin/sh",
            "-c",
            f"while true; do date > {DATE_OUTPUT_PATH}; sleep {REFRESH_INTERVAL_SEC}; done &",
        )
        yield self._ctx.commit()

    async def run(self):
        while True:
            await asyncio.sleep(REFRESH_INTERVAL_SEC)
            self._ctx.run(
                "/bin/sh",
                "-c",
                f"cat {DATE_OUTPUT_PATH}",
            )

            future_results = yield self._ctx.commit()
            results = await future_results
            print(results[0].stdout.strip())


async def main():
    async with Golem(budget=1.0, subnet_tag="devnet-beta.2") as golem:
        cluster = await golem.run_service(DateService, num_instances=1)
        start_time = datetime.now()

        while datetime.now() < start_time + timedelta(minutes=1):
            for num, instance in enumerate(cluster.instances):
                print(f"Instance {num} is {instance.state.value} on {instance.provider_name}")
        await asyncio.sleep(REFRESH_INTERVAL_SEC)
```

## yapapi.services

Implementation of high-level services API.

### ServiceState Objects

```python
class ServiceState(statemachine.StateMachine)
```

State machine describing the state and lifecycle of a Service instance.

### ServiceSignal Objects

```python
@dataclass
class ServiceSignal()
```

Simple container to carry information between the client code and the Service instance.

### Service Objects

```python
class Service()
```

Base class for service specifications.

To be extended by application developers to define their own, specialized Service specifications.

#### \_\_init\_\_

```python
 | __init__(cluster: "Cluster", ctx: WorkContext)
```

Initialize the service instance for a specific Cluster and a specific WorkContext.

**Arguments**:

* `cluster`: a cluster to which this service instance of this service belongs
* `ctx`: a work context object for executing commands on a provider that runs this

  service instance.

#### id

```python
 | @property
 | id()
```

Return the id of this service instance.

Guaranteed to be unique within a Cluster.

#### provider\_name

```python
 | @property
 | provider_name()
```

Return the name of the provider that runs this service instance.

#### send\_message

```python
 | async send_message(message: Any = None)
```

Send a control message to this instance.

#### send\_message\_nowait

```python
 | send_message_nowait(message: Optional[Any] = None)
```

Send a control message to this instance without blocking.

May raise `asyncio.QueueFull` if the channel for sending control messages is full.

#### receive\_message

```python
 | async receive_message() -> ServiceSignal
```

Wait for a control message sent to this instance.

#### receive\_message\_nowait

```python
 | receive_message_nowait() -> Optional[ServiceSignal]
```

Retrieve a control message sent to this instance.

Return `None` if no message is available.

#### get\_payload

```python
 | @staticmethod
 | async get_payload() -> Optional[Payload]
```

Return the payload \(runtime\) definition for this service.

If `get_payload` is not implemented, the payload will need to be provided in the `Golem.run_service` call.

#### start

```python
 | async start()
```

Implement the `starting` state of the service.

#### run

```python
 | async run()
```

Implement the `running` state of the service.

#### shutdown

```python
 | async shutdown()
```

Implement the `stopping` state of the service.

#### is\_available

```python
 | @property
 | is_available()
```

Return `True` iff this instance is available \(that is, starting, running or stopping\).

#### state

```python
 | @property
 | state()
```

Return the current state of this instance.

### ControlSignal Objects

```python
class ControlSignal(enum.Enum)
```

Control signal, used to request an instance's state change from the controlling Cluster.

### ServiceInstance Objects

```python
@dataclass
class ServiceInstance()
```

Cluster's service instance.

A binding between the instance of the Service, its control queue and its state, used by the Cluster to hold the complete state of each instance of a service.

#### state

```python
 | @property
 | state() -> ServiceState
```

Return the current state of this instance.

### Cluster Objects

```python
class Cluster(AsyncContextManager)
```

Golem's sub-engine used to spawn and control instances of a single Service.

#### \_\_init\_\_

```python
 | __init__(engine: "_Engine", service_class: Type[Service], payload: Payload, num_instances: int = 1, expiration: Optional[datetime] = None)
```

Initialize this Cluster.

**Arguments**:

* `engine`: an engine for running service instance
* `service_class`: service specification
* `payload`: definition of service runtime for this Cluster
* `num_instances`: number of instances to spawn in this Cluster
* `expiration`: a date before which all agreements related to running services

  in this Cluster should be terminated

#### \_\_aenter\_\_

```python
 | async __aenter__()
```

Post a Demand and start collecting provider Offers for running service instances.

#### \_\_aexit\_\_

```python
 | async __aexit__(exc_type, exc_val, exc_tb)
```

Release resources used by this Cluster.

#### emit

```python
 | emit(event: events.Event) -> None
```

Emit an event using this Cluster's engine.

#### instances

```python
 | @property
 | instances() -> List[Service]
```

Return the list of service instances in this Cluster.

#### get\_state

```python
 | get_state(service: Service) -> ServiceState
```

Return the state of the specific instance in this Cluster.

#### spawn\_instance

```python
 | async spawn_instance() -> None
```

Spawn a new service instance within this Cluster.

#### stop\_instance

```python
 | stop_instance(service: Service)
```

Stop the specific service instance belonging to this Cluster.

#### spawn\_instances

```python
 | spawn_instances(num_instances: Optional[int] = None) -> None
```

Spawn new instances within this Cluster.

**Arguments**:

* `num_instances`: number of instances to commission.

  if not given, spawns the number that the Cluster has been initialized with.

#### stop

```python
 | stop()
```

Signal the whole cluster to stop.

## yapapi.agreements\_pool

### BufferedAgreement Objects

```python
@dataclass
class BufferedAgreement()
```

Confirmed agreement with additional local metadata

### AgreementsPool Objects

```python
class AgreementsPool()
```

Manages proposals and agreements pool

#### cycle

```python
 | async cycle()
```

Performs cyclic tasks.

Should be called regularly.

#### add\_proposal

```python
 | async add_proposal(score: float, proposal: OfferProposal) -> None
```

Adds providers' proposal to the pool of available proposals

#### use\_agreement

```python
 | async use_agreement(cbk)
```

Gets an agreement and performs cbk\(\) on it

#### release\_agreement

```python
 | async release_agreement(agreement_id: str, allow_reuse: bool = True) -> None
```

Marks agreement as unused.

If the agreement supports multiple activities and `allow_reuse` is set then it will be returned to the pool and will be available for reuse. Otherwise it will be removed from the pool.

#### terminate\_all

```python
 | async terminate_all(reason: dict) -> None
```

Terminate all agreements.

#### on\_agreement\_terminated

```python
 | async on_agreement_terminated(agr_id: str, reason: dict) -> None
```

Reacts to agreement termination event

Should be called when AgreementTerminated event is received.

#### rejected\_last\_agreement

```python
 | rejected_last_agreement(provider_id: str) -> bool
```

Return `True` iff the last agreement proposed to `provider_id` has been rejected.

## yapapi.payload

### Payload Objects

```python
class Payload(AutodecoratingModel,  abc.ABC)
```

Base class for descriptions of the payload required by the requestor.

example:

```python
>>> import asyncio
>>>
>>> from dataclasses import dataclass
>>>
>>> from yapapi.props.builder import DemandBuilder
>>> from yapapi.props.base import prop, constraint
>>> from yapapi.props import inf
>>>
>>> from yapapi.payload import Payload
>>>
>>>
>>> TURBOGETH_RUNTIME_NAME = "turbogeth-managed"
>>> PROP_TURBOGETH_CHAIN = "golem.srv.app.eth.chain"
>>>
>>>
>>> @dataclass
... class TurbogethPayload(Payload):
...     chain: str = prop(PROP_TURBOGETH_CHAIN, default="rinkeby")
...     runtime: str = constraint(inf.INF_RUNTIME_NAME, default=TURBOGETH_RUNTIME_NAME)
...     min_mem_gib: float = constraint(inf.INF_MEM, operator=">=", default=16)
...     min_storage_gib: float = constraint(inf.INF_STORAGE, operator=">=", default=1024)
...
>>>
>>> async def main():
...     builder = DemandBuilder()
...     payload = TurbogethPayload(chain="mainnet", min_mem_gib=32)
...     await builder.decorate(payload)
...     print(builder)
...
>>> asyncio.run(main())
{'properties': {'golem.srv.app.eth.chain': 'mainnet'}, 'constraints': ['(&(golem.runtime.name=turbogeth-managed)\n\t(golem.inf.mem.gib>=32)\n\t(golem.inf.storage.gib>=1024))']}
```

## yapapi.payload.package

### PackageException Objects

```python
class PackageException(Exception)
```

Exception raised on any problems related to the package repository.

### Package Objects

```python
@dataclass
class Package(Payload)
```

Description of a task package \(e.g. a VM image\) deployed on the provider nodes

#### resolve\_url

```python
 | @abc.abstractmethod
 | async resolve_url() -> str
```

Return package URL.

## yapapi.payload.vm

#### repo

```python
async repo(*, image_hash: str, min_mem_gib: float = 0.5, min_storage_gib: float = 2.0) -> Package
```

Build a reference to application package.

**Arguments**:

* `image_hash`: hash of the package's image
* `min_mem_gib`: minimal memory required to execute application code
* `min_storage_gib`: minimal disk storage to execute tasks

**Returns**:

the payload definition for the given VM image

#### resolve\_repo\_srv

```python
resolve_repo_srv(repo_srv, fallback_url=_FALLBACK_REPO_URL) -> str
```

Get the url of the package repository based on its SRV record address.

**Arguments**:

* `repo_srv`: the SRV domain name
* `fallback_url`: temporary hardcoded fallback url in case there's a problem resolving SRV

**Returns**:

the url of the package repository containing the port :raises: PackageException if no valid service could be reached

## yapapi.utils

Utility functions and classes used within the `yapapi.executor` package.

### AsyncWrapper Objects

```python
class AsyncWrapper(AsyncContextManager)
```

Wraps a given callable to provide asynchronous calls.

Example usage:

with AsyncWrapper\(func\) as wrapper: wrapper.async\_call\("Hello", world=True\) wrapper.async\_call\("Bye!"\)

The above code will make two asynchronous calls to `func`. The results of the calls, if any, are discarded, so this class is most useful for wrapping callables that return `None`.

#### \_\_aexit\_\_

```python
 | async __aexit__(exc_type, exc_val, exc_tb) -> Optional[bool]
```

Stop the wrapper, process queued calls but do not accept any new ones.

#### async\_call

```python
 | async_call(*args, **kwargs) -> None
```

Schedule an asynchronous call to the wrapped callable.

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

Stops exposing GFTP urls created by [publish\(files=\[..\]\)](https://github.com/golemfactory/yagna-docs/tree/c108a1e4cd5d512edf56b04547e813e367018a11/yapapi/%60publish%60/README.md).

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

## yapapi.storage.webdav

## yapapi.props

### NodeInfo Objects

```python
@dataclass
class NodeInfo(Model)
```

Properties describing the information regarding the node.

#### name

human-readable name of the Golem node

#### subnet\_tag

the name of the subnet within which the Demands and Offers are matched

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

#### multi\_activity

Whether client supports multi\_activity \(executing more than one activity per agreement\).

## yapapi.props.builder

### DemandBuilder Objects

```python
class DemandBuilder()
```

Builds a dictionary of properties and constraints from high-level models.

The dictionary represents a Demand object, which is later matched by the new Golem's market implementation against Offers coming from providers to find those providers who can satisfy the requestor's demand.

example usage:

```python
>>> import yapapi
>>> from yapapi import props as yp
>>> from yapapi.props.builder import DemandBuilder
>>> from datetime import datetime, timezone
>>> builder = DemandBuilder()
>>> builder.add(yp.NodeInfo(name="a node", subnet_tag="testnet"))
>>> builder.add(yp.Activity(expiration=datetime.now(timezone.utc)))
>>> builder.__repr__
>>> print(builder)
{'properties':
    {'golem.node.id.name': 'a node',
     'golem.node.debug.subnet': 'testnet',
     'golem.srv.comp.expiration': 1601655628772},
 'constraints': []}
```

#### properties

```python
 | @property
 | properties() -> dict
```

List of properties for this demand.

#### constraints

```python
 | @property
 | constraints() -> str
```

Constraints definition for this demand.

#### ensure

```python
 | ensure(constraint: str)
```

Add a constraint to the demand definition.

#### add

```python
 | add(m: Model)
```

Add properties from the specified model to this demand definition.

#### subscribe

```python
 | async subscribe(market: Market) -> Subscription
```

Create a Demand on the market and subscribe to Offers that will match that Demand.

### DemandDecorator Objects

```python
class DemandDecorator(abc.ABC)
```

An interface that specifies classes that can add properties and constraints through a DemandBuilder

#### decorate\_demand

```python
 | @abc.abstractmethod
 | async decorate_demand(demand: DemandBuilder)
```

Add appropriate properties and constraints to a Demand

### AutodecoratingModel Objects

```python
class AutodecoratingModel(Model,  DemandDecorator)
```

Base class, implementing the DemandDecorator interface to automatically decorate a demand using the model's properties and constraints.

example:

```python
>>> import asyncio
>>> from dataclasses import dataclass
>>> from yapapi.props import prop, constraint
>>> from yapapi.props.builder import AutodecoratingModel, DemandBuilder
>>>
>>> @dataclass
... class Foo(AutodecoratingModel):
...     bar: str = prop("some.bar")
...     max_baz: int = constraint("baz", "<=", 100)
...
>>> async def main():
...     foo = Foo(bar="a nice one", max_baz=50)
...     demand = DemandBuilder()
...     await foo.decorate_demand(demand)
...     print(demand)
...
>>> asyncio.run(main())
{'properties': {'some.bar': 'a nice one'}, 'constraints': ['((baz<=50))']}
```

## yapapi.props.com

Payment-related properties.

## yapapi.props.inf

Infrastructural properties.

## yapapi.props.base

### InvalidPropertiesError Objects

```python
class InvalidPropertiesError(Exception)
```

Raised by `Model.from_properties(cls, properties)` when given invalid `properties`.

### Model Objects

```python
class Model(abc.ABC)
```

Base class from which all property models inherit.

Provides helper methods to load the property model data from a dictionary and to get a mapping of all the keys available in the given model.

#### property\_fields

```python
 | @classmethod
 | property_fields(cls) -> typing.List[Field]
```

Return a list of property fields of a Model.

For the sake of backwards-compatibility, assumes that fields with no defined ModelFieldType are properties.

#### constraint\_fields

```python
 | @classmethod
 | constraint_fields(cls) -> typing.List[Field]
```

Return a list of constraint fields of a Model.

#### from\_properties

```python
 | @classmethod
 | from_properties(cls: Type[ME], props: Props) -> ME
```

Initialize the model from a dictionary representation.

When provided with a dictionary of properties, it will find the matching keys within it and fill the model fields with the values from the dictionary.

It ignores non-matching keys - i.e. doesn't require filtering of the properties' dictionary before the model is fed with the data. Thus, several models can be initialized from the same dictionary and all models will only load their own data.

#### property\_keys

```python
 | @classmethod
 | property_keys(cls)
```

**Returns**:

a mapping between the model's field names and the property keys

example:

```python
>>> import dataclasses
>>> import typing
>>> from yapapi.props.base import Model
>>> @dataclasses.dataclass
... class NodeInfo(Model):
...     name: typing.Optional[str] = \
...     dataclasses.field(default=None, metadata={"key": "golem.node.id.name"})
...
>>> NodeInfo.property_keys().name
'golem.node.id.name'
```

#### constraint

```python
constraint(key: str, operator: ConstraintOperator = "=", default=MISSING)
```

Return a constraint-type dataclass field for a Model.

**Arguments**:

* `key`: the key of the property on which the constraint is made - e.g. "golem.srv.comp.task\_package"
* `operator`: constraint's operator, one of: "=", "&gt;=", "&lt;="
* `default`: the default value for the constraint

example:

```python
>>> from dataclasses import dataclass
>>> from yapapi.props.base import Model, constraint, constraint_model_serialize
>>>
>>> @dataclass
... class Foo(Model):
...     max_baz: int = constraint("baz", "<=", 100)
...
>>> constraints = constraint_model_serialize(Foo())
>>> print(constraints)
['(baz<=100)']
```

#### prop

```python
prop(key: str, default=MISSING)
```

Return a property-type dataclass field for a Model.

**Arguments**:

* `key`: the key of the property, e.g. "golem.runtime.name"
* `default`: the default value of the property

example:

```python
>>> from dataclasses import dataclass
>>> from yapapi.props.base import Model, prop
>>> from yapapi.props.builder import DemandBuilder
>>>
>>> @dataclass
... class Foo(Model):
...     bar: int = prop("bar", default=100)
...
>>> builder = DemandBuilder()
>>> builder.add(Foo(bar=42))
>>> print(builder.properties)
{'bar': 42}
```

#### constraint\_to\_str

```python
constraint_to_str(value, f: Field) -> str
```

Get string representation of a constraint with a given value.

**Arguments**:

* `value`: the value of the the constraint field
* `f`: the dataclass field for this constraint

#### constraint\_model\_serialize

```python
constraint_model_serialize(m: Model) -> List[str]
```

Return a list of stringified constraints on the given Model instance.

**Arguments**:

* `m`: instance of Model for which we want the constraints serialized

#### join\_str\_constraints

```python
join_str_constraints(constraints: List[str], operator: ConstraintGroupOperator = "&") -> str
```

Join a list of constraints using the given opererator.

The semantics here reflect LDAP filters: [https://ldap.com/ldap-filters/](https://ldap.com/ldap-filters/)

**Arguments**:

* `constraints`: list of strings representing individual constraints

  \(which may include previously joined constraint groups\)

* `operator`: constraint group operator, one of "&", "\|", "!", which represent

  "and", "or" and "not" operations on those constraints.

  "!" requires that the list contains one and only one constraint.

  Defaults to "&" \(and\) if not given.

**Returns**:

string representation of the compound constraint.

example:

```python
>>> from dataclasses import dataclass
>>> from yapapi.props.base import Model, constraint, constraint_model_serialize, join_str_constraints
>>>
>>> @dataclass
... class Foo(Model):
...     min_bar: int = constraint("bar", ">=", 42)
...     max_bar: int = constraint("bar", "<=", 128)
...
>>> print(join_str_constraints(constraint_model_serialize(Foo())))
(&(bar>=42)
(bar<=128))
```

## yapapi.events

Representing events in Golem computation.

### Event Objects

```python
@dataclass(init=False)
class Event()
```

An abstract base class for types of events emitted by `Executor.submit()`.

#### extract\_exc\_info

```python
 | extract_exc_info() -> Tuple[Optional[ExcInfo], "Event"]
```

Extract exception information from this event.

Return the extracted exception information and a copy of the event without the exception information.

### HasExcInfo Objects

```python
@dataclass(init=False)
class HasExcInfo(Event)
```

A base class for types of events that carry an optional exception info.

#### extract\_exc\_info

```python
 | extract_exc_info() -> Tuple[Optional[ExcInfo], "Event"]
```

Return the `exc_info` field and a copy of this event with the field set to `None`.

### ComputationFinished Objects

```python
@dataclass
class ComputationFinished(HasExcInfo,  ComputationEvent)
```

Indicates successful completion if `exc_info` is `None` and a failure otherwise.

### WorkerFinished Objects

```python
@dataclass
class WorkerFinished(HasExcInfo,  AgreementEvent)
```

Indicates successful completion if `exc_info` is `None` and a failure otherwise.

### ShutdownFinished Objects

```python
@dataclass
class ShutdownFinished(HasExcInfo)
```

Indicates the completion of Executor shutdown sequence

## examples

## examples.utils

Utilities for yapapi example scripts.

