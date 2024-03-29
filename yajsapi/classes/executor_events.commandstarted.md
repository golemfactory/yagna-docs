# Class: CommandStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandStarted

## Class: CommandStarted

[executor/events](../modules/executor_events.md).CommandStarted

### Hierarchy

* [CommandEvent](executor_events.commandevent.md)

  ↳ **CommandStarted**

### Table of contents

#### Constructors

* [constructor](executor_events.commandstarted.md#constructor)

#### Properties

* [agr\_id](executor_events.commandstarted.md#agr_id)
* [cmd\_idx](executor_events.commandstarted.md#cmd_idx)
* [command](executor_events.commandstarted.md#command)
* [task\_id](executor_events.commandstarted.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandstarted.md#extract_exc_info)

### Constructors

#### constructor

• **new CommandStarted**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Inherited from**

[CommandEvent](executor_events.commandevent.md).[constructor](executor_events.commandevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:314](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L314)

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

• **command**: `string`

**Defined in**

[yajsapi/executor/events.ts:449](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L449)

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

