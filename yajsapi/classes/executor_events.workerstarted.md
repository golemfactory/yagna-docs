# Class: WorkerStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / WorkerStarted

## Class: WorkerStarted

[executor/events](../modules/executor_events.md).WorkerStarted

### Hierarchy

* _AgreementEvent_

  ↳ **WorkerStarted**

### Table of contents

#### Constructors

* [constructor](executor_events.workerstarted.md#constructor)

#### Properties

* [agr\_id](executor_events.workerstarted.md#agr_id)

#### Methods

* [extract\_exc\_info](executor_events.workerstarted.md#extract_exc_info)

### Constructors

#### constructor

* **new WorkerStarted**\(`__namedParameters`: _Object_\): [_WorkerStarted_](executor_events.workerstarted.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_WorkerStarted_](executor_events.workerstarted.md)

Defined in: [yajsapi/executor/events.ts:218](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L218)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

