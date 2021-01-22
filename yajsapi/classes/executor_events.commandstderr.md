[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / CommandStdErr

# Class: CommandStdErr

[executor/events](../modules/executor_events.md).CommandStdErr

## Hierarchy

* [*CommandEvent*](executor_events.commandevent.md)

  ↳ **CommandStdErr**

## Table of contents

### Constructors

- [constructor](executor_events.commandstderr.md#constructor)

### Properties

- [agr\_id](executor_events.commandstderr.md#agr_id)
- [cmd\_idx](executor_events.commandstderr.md#cmd_idx)
- [output](executor_events.commandstderr.md#output)
- [task\_id](executor_events.commandstderr.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.commandstderr.md#extract_exc_info)

## Constructors

### constructor

\+ **new CommandStdErr**(`__namedParameters`: *Object*): [*CommandStdErr*](executor_events.commandstderr.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*CommandStdErr*](executor_events.commandstderr.md)

Inherited from: [CommandEvent](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:431](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L431)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Inherited from: [CommandEvent](executor_events.commandevent.md).[agr_id](executor_events.commandevent.md#agr_id)

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### cmd\_idx

• **cmd\_idx**: *number*

Inherited from: [CommandEvent](executor_events.commandevent.md).[cmd_idx](executor_events.commandevent.md#cmd_idx)

Defined in: [yajsapi/executor/events.ts:297](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L297)

___

### output

• **output**: *string*

Defined in: [yajsapi/executor/events.ts:431](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L431)

___

### task\_id

• `Optional` **task\_id**: *undefined* \| *null* \| *string*

Inherited from: [CommandEvent](executor_events.commandevent.md).[task_id](executor_events.commandevent.md#task_id)

Defined in: [yajsapi/executor/events.ts:267](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L267)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [CommandEvent](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
