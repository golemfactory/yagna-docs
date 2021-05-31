# Class: CollectFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CollectFailed

## Class: CollectFailed

[executor/events](../modules/executor_events.md).CollectFailed

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **CollectFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.collectfailed.md#constructor)

#### Properties

* [reason](executor_events.collectfailed.md#reason)
* [sub\_id](executor_events.collectfailed.md#sub_id)

#### Methods

* [extract\_exc\_info](executor_events.collectfailed.md#extract_exc_info)

### Constructors

#### constructor

* **new CollectFailed**\(`__namedParameters`: _Object_\): [_CollectFailed_](executor_events.collectfailed.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_CollectFailed_](executor_events.collectfailed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L57)

### Properties

#### reason

• **reason**: _string_

Defined in: [yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L57)

#### sub\_id

• **sub\_id**: _string_

Defined in: [yajsapi/executor/events.ts:56](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L56)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

