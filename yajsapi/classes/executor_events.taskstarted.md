# Class: TaskStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / TaskStarted

## Class: TaskStarted

[executor/events](../modules/executor_events.md).TaskStarted

### Hierarchy

* `EventGeneral`

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

• **new TaskStarted**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

EventGeneral.constructor

**Defined in**

[yajsapi/executor/events.ts:253](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L253)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

EventGeneral.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### task\_data

• `Optional` **task\_data**: `any`

**Defined in**

[yajsapi/executor/events.ts:253](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L253)

#### task\_id

• `Optional` **task\_id**: `string`

**Inherited from**

EventGeneral.task\_id

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

EventGeneral.extract\_exc\_info

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

