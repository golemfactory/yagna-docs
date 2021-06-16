# Class: ScriptSent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ScriptSent

## Class: ScriptSent

[executor/events](../modules/executor_events.md).ScriptSent

### Hierarchy

* `ScriptEvent`

  ↳ **ScriptSent**

### Table of contents

#### Constructors

* [constructor](executor_events.scriptsent.md#constructor)

#### Properties

* [agr\_id](executor_events.scriptsent.md#agr_id)
* [cmds](executor_events.scriptsent.md#cmds)
* [task\_id](executor_events.scriptsent.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.scriptsent.md#extract_exc_info)

### Constructors

#### constructor

• **new ScriptSent**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

ScriptEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:288](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L288)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

ScriptEvent.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### cmds

• `Optional` **cmds**: `any`

**Defined in**

[yajsapi/executor/events.ts:288](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L288)

#### task\_id

• `Optional` **task\_id**: `null` \| `string`

**Inherited from**

ScriptEvent.task\_id

**Defined in**

[yajsapi/executor/events.ts:284](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L284)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns**

\[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

**Inherited from**

ScriptEvent.extract\_exc\_info

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

