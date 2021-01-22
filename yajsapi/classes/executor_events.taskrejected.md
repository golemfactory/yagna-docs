[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / TaskRejected

# Class: TaskRejected

[executor/events](../modules/executor_events.md).TaskRejected

## Hierarchy

* *TaskEvent*

  ↳ **TaskRejected**

## Table of contents

### Constructors

- [constructor](executor_events.taskrejected.md#constructor)

### Properties

- [reason](executor_events.taskrejected.md#reason)
- [task\_id](executor_events.taskrejected.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.taskrejected.md#extract_exc_info)

## Constructors

### constructor

\+ **new TaskRejected**(`__namedParameters`: *Object*): [*TaskRejected*](executor_events.taskrejected.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*TaskRejected*](executor_events.taskrejected.md)

Defined in: [yajsapi/executor/events.ts:449](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L449)

## Properties

### reason

• `Optional` **reason**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:449](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L449)

___

### task\_id

• `Optional` **task\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:227](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L227)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
