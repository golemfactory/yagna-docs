[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / CommandEventContext

# Class: CommandEventContext

[executor/events](../modules/executor_events.md).CommandEventContext

## Hierarchy

* **CommandEventContext**

## Table of contents

### Constructors

- [constructor](executor_events.commandeventcontext.md#constructor)

### Properties

- [evt](executor_events.commandeventcontext.md#evt)

### Methods

- [computation\_finished](executor_events.commandeventcontext.md#computation_finished)
- [event](executor_events.commandeventcontext.md#event)
- [fromJson](executor_events.commandeventcontext.md#fromjson)

## Constructors

### constructor

\+ **new CommandEventContext**(`evt_cls`: *any*): [*CommandEventContext*](executor_events.commandeventcontext.md)

#### Parameters:

Name | Type |
------ | ------ |
`evt_cls` | *any* |

**Returns:** [*CommandEventContext*](executor_events.commandeventcontext.md)

Defined in: [yajsapi/executor/events.ts:335](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L335)

## Properties

### evt

• **evt**: [*CommandEvent*](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:335](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L335)

## Methods

### computation\_finished

▸ **computation_finished**(`last_idx`: *any*): *boolean*

#### Parameters:

Name | Type |
------ | ------ |
`last_idx` | *any* |

**Returns:** *boolean*

Defined in: [yajsapi/executor/events.ts:389](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L389)

___

### event

▸ **event**(`agr_id`: *string*, `task_id`: *string*, `cmds`: *any*[]): [*CommandEvent*](executor_events.commandevent.md)

#### Parameters:

Name | Type |
------ | ------ |
`agr_id` | *string* |
`task_id` | *string* |
`cmds` | *any*[] |

**Returns:** [*CommandEvent*](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:399](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L399)

___

### fromJson

▸ `Static`**fromJson**(`json`: *string*): [*CommandEventContext*](executor_events.commandeventcontext.md)

#### Parameters:

Name | Type |
------ | ------ |
`json` | *string* |

**Returns:** [*CommandEventContext*](executor_events.commandeventcontext.md)

Defined in: [yajsapi/executor/events.ts:340](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L340)
