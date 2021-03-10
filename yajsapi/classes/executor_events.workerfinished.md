# Class: WorkerFinished

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / WorkerFinished

## Class: WorkerFinished

[executor/events](../modules/executor_events.md).WorkerFinished

### Hierarchy

* _AgreementEvent_

  ↳ **WorkerFinished**

### Table of contents

#### Constructors

* [constructor](executor_events.workerfinished.md#constructor)

#### Properties

* [agr\_id](executor_events.workerfinished.md#agr_id)
* [exception](executor_events.workerfinished.md#exception)

#### Methods

* [extract\_exc\_info](executor_events.workerfinished.md#extract_exc_info)

### Constructors

#### constructor

* **new WorkerFinished**\(`__namedParameters`: _Object_\): [_WorkerFinished_](executor_events.workerfinished.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_WorkerFinished_](executor_events.workerfinished.md)

Defined in: [yajsapi/executor/events.ts:262](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L262)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### exception

• `Optional` **exception**: _undefined_ \| _null_ \| Error= null

Defined in: [yajsapi/executor/events.ts:262](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L262)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Defined in: [yajsapi/executor/events.ts:270](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L270)

