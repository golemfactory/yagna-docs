# Class: GettingResults

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / GettingResults

## Class: GettingResults

[executor/events](../modules/executor_events.md).GettingResults

### Hierarchy

* _ScriptEvent_

  ↳ **GettingResults**

### Table of contents

#### Constructors

* [constructor](executor_events.gettingresults.md#constructor)

#### Properties

* [agr\_id](executor_events.gettingresults.md#agr_id)
* [task\_id](executor_events.gettingresults.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.gettingresults.md#extract_exc_info)

### Constructors

#### constructor

* **new GettingResults**\(`__namedParameters`: _Object_\): [_GettingResults_](executor_events.gettingresults.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_GettingResults_](executor_events.gettingresults.md)

Defined in: [yajsapi/executor/events.ts:295](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L295)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### task\_id

• `Optional` **task\_id**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:282](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L282)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

