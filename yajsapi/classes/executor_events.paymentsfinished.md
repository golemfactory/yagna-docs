# Class: PaymentsFinished

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / PaymentsFinished

## Class: PaymentsFinished

[executor/events](../modules/executor_events.md).PaymentsFinished

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **PaymentsFinished**

### Table of contents

#### Constructors

* [constructor](executor_events.paymentsfinished.md#constructor)

#### Methods

* [extract\_exc\_info](executor_events.paymentsfinished.md#extract_exc_info)

### Constructors

#### constructor

* **new PaymentsFinished**\(\): [_PaymentsFinished_](executor_events.paymentsfinished.md)

**Returns:** [_PaymentsFinished_](executor_events.paymentsfinished.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L9)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

