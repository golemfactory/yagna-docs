[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / YaEvent

# Class: YaEvent

[executor/events](../modules/executor_events.md).YaEvent

An abstract base class for types of events emitted by `Executor.submit()`.

## Hierarchy

* **YaEvent**

  ↳ [*ComputationStarted*](executor_events.computationstarted.md)

  ↳ [*ComputationFinished*](executor_events.computationfinished.md)

  ↳ [*ComputationFailed*](executor_events.computationfailed.md)

  ↳ [*PaymentsFinished*](executor_events.paymentsfinished.md)

  ↳ [*SubscriptionCreated*](executor_events.subscriptioncreated.md)

  ↳ [*SubscriptionFailed*](executor_events.subscriptionfailed.md)

  ↳ [*CollectFailed*](executor_events.collectfailed.md)

  ↳ [*NoProposalsConfirmed*](executor_events.noproposalsconfirmed.md)

  ↳ [*DownloadStarted*](executor_events.downloadstarted.md)

  ↳ [*DownloadFinished*](executor_events.downloadfinished.md)

## Table of contents

### Constructors

- [constructor](executor_events.yaevent.md#constructor)

### Methods

- [extract\_exc\_info](executor_events.yaevent.md#extract_exc_info)

## Constructors

### constructor

\+ **new YaEvent**(): [*YaEvent*](executor_events.yaevent.md)

**Returns:** [*YaEvent*](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L9)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
