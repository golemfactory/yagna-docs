# Class: CommandEvent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandEvent

## Class: CommandEvent

[executor/events](../modules/executor_events.md).CommandEvent

### Hierarchy

* `ScriptEvent`

  ↳ **CommandEvent**

  ↳↳ [CommandExecuted](executor_events.commandexecuted.md)

  ↳↳ [CommandStarted](executor_events.commandstarted.md)

  ↳↳ [CommandStdOut](executor_events.commandstdout.md)

  ↳↳ [CommandStdErr](executor_events.commandstderr.md)

### Table of contents

#### Constructors

* [constructor](executor_events.commandevent.md#constructor)

#### Properties

* [agr\_id](executor_events.commandevent.md#agr_id)
* [cmd\_idx](executor_events.commandevent.md#cmd_idx)
* [task\_id](executor_events.commandevent.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandevent.md#extract_exc_info)

### Constructors

#### constructor

• **new CommandEvent**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

ScriptEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:314](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L314)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

ScriptEvent.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### cmd\_idx

• **cmd\_idx**: `number`

**Defined in**

[yajsapi/executor/events.ts:314](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L314)

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

