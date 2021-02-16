# Class: YaEvent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / YaEvent

## Class: YaEvent

[executor/events](../modules/executor_events.md).YaEvent

An abstract base class for types of events emitted by `Executor.submit()`.

### Hierarchy

* **YaEvent**

  ↳ [_ComputationStarted_](executor_events.computationstarted.md)

  ↳ [_ComputationFinished_](executor_events.computationfinished.md)

  ↳ [_ComputationFailed_](executor_events.computationfailed.md)

  ↳ [_PaymentsFinished_](executor_events.paymentsfinished.md)

  ↳ [_SubscriptionCreated_](executor_events.subscriptioncreated.md)

  ↳ [_SubscriptionFailed_](executor_events.subscriptionfailed.md)

  ↳ [_CollectFailed_](executor_events.collectfailed.md)

  ↳ [_NoProposalsConfirmed_](executor_events.noproposalsconfirmed.md)

  ↳ [_DownloadStarted_](executor_events.downloadstarted.md)

  ↳ [_DownloadFinished_](executor_events.downloadfinished.md)

### Table of contents

#### Constructors

* [constructor](executor_events.yaevent.md#constructor)

#### Methods

* [extract\_exc\_info](executor_events.yaevent.md#extract_exc_info)

### Constructors

#### constructor

+ **new YaEvent**\(\): [_YaEvent_](executor_events.yaevent.md)

**Returns:** [_YaEvent_](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L9)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

