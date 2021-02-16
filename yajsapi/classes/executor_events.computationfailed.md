# Class: ComputationFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ComputationFailed

## Class: ComputationFailed

[executor/events](../modules/executor_events.md).ComputationFailed

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **ComputationFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.computationfailed.md#constructor)

#### Properties

* [reason](executor_events.computationfailed.md#reason)

#### Methods

* [extract\_exc\_info](executor_events.computationfailed.md#extract_exc_info)

### Constructors

#### constructor

+ **new ComputationFailed**\(\): [_ComputationFailed_](executor_events.computationfailed.md)

**Returns:** [_ComputationFailed_](executor_events.computationfailed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L9)

### Properties

#### reason

• `Optional` **reason**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L34)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

