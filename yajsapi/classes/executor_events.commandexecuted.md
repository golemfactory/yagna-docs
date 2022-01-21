# Class: CommandExecuted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandExecuted

## Class: CommandExecuted

[executor/events](../modules/executor_events.md).CommandExecuted

### Hierarchy

* [CommandEvent](executor_events.commandevent.md)

  ↳ **CommandExecuted**

### Table of contents

#### Constructors

* [constructor](executor_events.commandexecuted.md#constructor)

#### Properties

* [agr\_id](executor_events.commandexecuted.md#agr_id)
* [cmd\_idx](executor_events.commandexecuted.md#cmd_idx)
* [command](executor_events.commandexecuted.md#command)
* [message](executor_events.commandexecuted.md#message)
* [stderr](executor_events.commandexecuted.md#stderr)
* [stdout](executor_events.commandexecuted.md#stdout)
* [success](executor_events.commandexecuted.md#success)
* [task\_id](executor_events.commandexecuted.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandexecuted.md#extract_exc_info)

### Constructors

#### constructor

• **new CommandExecuted**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

[CommandEvent](executor_events.commandevent.md).[constructor](executor_events.commandevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:328](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L328)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

[CommandEvent](executor_events.commandevent.md).[agr\_id](executor_events.commandevent.md#agr_id)

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### cmd\_idx

• **cmd\_idx**: `number`

**Inherited from**

[CommandEvent](executor_events.commandevent.md).[cmd\_idx](executor_events.commandevent.md#cmd_idx)

**Defined in**

[yajsapi/executor/events.ts:314](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L314)

#### command

• `Optional` **command**: `any`

**Defined in**

[yajsapi/executor/events.ts:324](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L324)

#### message

• `Optional` **message**: `string`

**Defined in**

[yajsapi/executor/events.ts:326](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L326)

#### stderr

• `Optional` **stderr**: `string`

**Defined in**

[yajsapi/executor/events.ts:328](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L328)

#### stdout

• `Optional` **stdout**: `string`

**Defined in**

[yajsapi/executor/events.ts:327](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L327)

#### success

• `Optional` **success**: `boolean`

**Defined in**

[yajsapi/executor/events.ts:325](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L325)

#### task\_id

• `Optional` **task\_id**: `null` \| `string`

**Inherited from**

[CommandEvent](executor_events.commandevent.md).[task\_id](executor_events.commandevent.md#task_id)

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

[CommandEvent](executor_events.commandevent.md).[extract\_exc\_info](executor_events.commandevent.md#extract_exc_info)

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

