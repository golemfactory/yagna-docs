# Class: TaskRejected

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / TaskRejected

## Class: TaskRejected

[executor/events](../modules/executor_events.md).TaskRejected

### Hierarchy

* _TaskEvent_

  ↳ **TaskRejected**

### Table of contents

#### Constructors

* [constructor](executor_events.taskrejected.md#constructor)

#### Properties

* [reason](executor_events.taskrejected.md#reason)
* [task\_id](executor_events.taskrejected.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.taskrejected.md#extract_exc_info)

### Constructors

#### constructor

+ **new TaskRejected**\(`__namedParameters`: _Object_\): [_TaskRejected_](executor_events.taskrejected.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_TaskRejected_](executor_events.taskrejected.md)

Defined in: [yajsapi/executor/events.ts:469](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L469)

### Properties

#### reason

• `Optional` **reason**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:469](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L469)

#### task\_id

• `Optional` **task\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:242](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L242)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

