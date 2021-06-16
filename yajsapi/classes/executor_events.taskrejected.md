# Class: TaskRejected

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / TaskRejected

## Class: TaskRejected

[executor/events](../modules/executor_events.md).TaskRejected

### Hierarchy

* `TaskEvent`

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

• **new TaskRejected**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

TaskEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:475](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L475)

### Properties

#### reason

• `Optional` **reason**: `null` \| `string`

**Defined in**

[yajsapi/executor/events.ts:475](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L475)

#### task\_id

• `Optional` **task\_id**: `string`

**Inherited from**

TaskEvent.task\_id

**Defined in**

[yajsapi/executor/events.ts:244](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L244)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns**

\[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

**Inherited from**

TaskEvent.extract\_exc\_info

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

