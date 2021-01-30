# executor/events/commandeventcontext

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / CommandEventContext

## Class: CommandEventContext

[executor/events](../yajsapi-2/executor_events.md).CommandEventContext

### Hierarchy

* **CommandEventContext**

### Table of contents

#### Constructors

* [constructor](executor_events.commandeventcontext.md#constructor)

#### Properties

* [evt](executor_events.commandeventcontext.md#evt)

#### Methods

* [computation\_finished](executor_events.commandeventcontext.md#computation_finished)
* [event](executor_events.commandeventcontext.md#event)
* [fromJson](executor_events.commandeventcontext.md#fromjson)

### Constructors

#### constructor

+ **new CommandEventContext**\(`evt_cls`: _any_\): [_CommandEventContext_](executor_events.commandeventcontext.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `evt_cls` | _any_ |

**Returns:** [_CommandEventContext_](executor_events.commandeventcontext.md)

Defined in: [yajsapi/executor/events.ts:320](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L320)

### Properties

#### evt

• **evt**: [_CommandEvent_](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:320](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L320)

### Methods

#### computation\_finished

▸ **computation\_finished**\(`last_idx`: _any_\): _boolean_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `last_idx` | _any_ |

**Returns:** _boolean_

Defined in: [yajsapi/executor/events.ts:369](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L369)

#### event

▸ **event**\(`agr_id`: _string_, `task_id`: _string_, `cmds`: _any_\[\]\): [_CommandEvent_](executor_events.commandevent.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `agr_id` | _string_ |
| `task_id` | _string_ |
| `cmds` | _any_\[\] |

**Returns:** [_CommandEvent_](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:379](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L379)

#### fromJson

▸ `Static`**fromJson**\(`json`: _string_\): [_CommandEventContext_](executor_events.commandeventcontext.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `json` | _string_ |

**Returns:** [_CommandEventContext_](executor_events.commandeventcontext.md)

Defined in: [yajsapi/executor/events.ts:325](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L325)

