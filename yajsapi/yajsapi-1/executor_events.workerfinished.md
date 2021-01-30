# executor/events/workerfinished

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / WorkerFinished

## Class: WorkerFinished

[executor/events](../yajsapi-2/executor_events.md).WorkerFinished

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

+ **new WorkerFinished**\(`__namedParameters`: _Object_\): [_WorkerFinished_](executor_events.workerfinished.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_WorkerFinished_](executor_events.workerfinished.md)

Defined in: [yajsapi/executor/events.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L247)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

#### exception

• `Optional` **exception**: _undefined_ \| _null_ \| Error= null

Defined in: [yajsapi/executor/events.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L247)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Defined in: [yajsapi/executor/events.ts:255](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L255)

