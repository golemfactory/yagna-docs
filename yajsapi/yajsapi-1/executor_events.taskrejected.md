# executor/events/taskrejected

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / TaskRejected

## Class: TaskRejected

[executor/events](../yajsapi-2/executor_events.md).TaskRejected

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

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_TaskRejected_](executor_events.taskrejected.md)

Defined in: [yajsapi/executor/events.ts:449](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L449)

### Properties

#### reason

• `Optional` **reason**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:449](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L449)

#### task\_id

• `Optional` **task\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:227](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L227)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)

