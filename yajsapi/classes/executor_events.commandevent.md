[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / CommandEvent

# Class: CommandEvent

[executor/events](../modules/executor_events.md).CommandEvent

## Hierarchy

* *ScriptEvent*

  ↳ **CommandEvent**

  ↳↳ [*CommandExecuted*](executor_events.commandexecuted.md)

  ↳↳ [*CommandStarted*](executor_events.commandstarted.md)

  ↳↳ [*CommandStdOut*](executor_events.commandstdout.md)

  ↳↳ [*CommandStdErr*](executor_events.commandstderr.md)

## Table of contents

### Constructors

- [constructor](executor_events.commandevent.md#constructor)

### Properties

- [agr\_id](executor_events.commandevent.md#agr_id)
- [cmd\_idx](executor_events.commandevent.md#cmd_idx)
- [task\_id](executor_events.commandevent.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.commandevent.md#extract_exc_info)

## Constructors

### constructor

\+ **new CommandEvent**(`__namedParameters`: *Object*): [*CommandEvent*](executor_events.commandevent.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*CommandEvent*](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:297](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L297)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### cmd\_idx

• **cmd\_idx**: *number*

Defined in: [yajsapi/executor/events.ts:297](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L297)

___

### task\_id

• `Optional` **task\_id**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:267](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L267)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
