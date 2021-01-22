[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / TaskStarted

# Class: TaskStarted

[executor/events](../modules/executor_events.md).TaskStarted

## Hierarchy

* *EventGeneral*

  ↳ **TaskStarted**

## Table of contents

### Constructors

- [constructor](executor_events.taskstarted.md#constructor)

### Properties

- [agr\_id](executor_events.taskstarted.md#agr_id)
- [task\_data](executor_events.taskstarted.md#task_data)
- [task\_id](executor_events.taskstarted.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.taskstarted.md#extract_exc_info)

## Constructors

### constructor

\+ **new TaskStarted**(`__namedParameters`: *Object*): [*TaskStarted*](executor_events.taskstarted.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*TaskStarted*](executor_events.taskstarted.md)

Defined in: [yajsapi/executor/events.ts:236](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L236)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### task\_data

• `Optional` **task\_data**: *any*

Defined in: [yajsapi/executor/events.ts:236](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L236)

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
