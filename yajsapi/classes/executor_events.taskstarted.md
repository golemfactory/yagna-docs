# Class: TaskStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / TaskStarted

## Class: TaskStarted

[executor/events](../modules/executor_events.md).TaskStarted

### Hierarchy

* _EventGeneral_

  ↳ **TaskStarted**

### Table of contents

#### Constructors

* [constructor](executor_events.taskstarted.md#constructor)

#### Properties

* [agr\_id](executor_events.taskstarted.md#agr_id)
* [task\_data](executor_events.taskstarted.md#task_data)
* [task\_id](executor_events.taskstarted.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.taskstarted.md#extract_exc_info)

### Constructors

#### constructor

* **new TaskStarted**\(`__namedParameters`: _Object_\): [_TaskStarted_](executor_events.taskstarted.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_TaskStarted_](executor_events.taskstarted.md)

Defined in: [yajsapi/executor/events.ts:251](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L251)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### task\_data

• `Optional` **task\_data**: _any_

Defined in: [yajsapi/executor/events.ts:251](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L251)

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

