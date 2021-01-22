[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / TaskAccepted

# Class: TaskAccepted

[executor/events](../modules/executor_events.md).TaskAccepted

## Hierarchy

* *TaskEvent*

  ↳ **TaskAccepted**

## Table of contents

### Constructors

- [constructor](executor_events.taskaccepted.md#constructor)

### Properties

- [result](executor_events.taskaccepted.md#result)
- [task\_id](executor_events.taskaccepted.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.taskaccepted.md#extract_exc_info)

## Constructors

### constructor

\+ **new TaskAccepted**(`__namedParameters`: *Object*): [*TaskAccepted*](executor_events.taskaccepted.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*TaskAccepted*](executor_events.taskaccepted.md)

Defined in: [yajsapi/executor/events.ts:440](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L440)

## Properties

### result

• `Optional` **result**: *any*

Defined in: [yajsapi/executor/events.ts:440](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L440)

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
