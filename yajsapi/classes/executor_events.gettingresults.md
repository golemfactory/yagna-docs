[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / GettingResults

# Class: GettingResults

[executor/events](../modules/executor_events.md).GettingResults

## Hierarchy

* *ScriptEvent*

  ↳ **GettingResults**

## Table of contents

### Constructors

- [constructor](executor_events.gettingresults.md#constructor)

### Properties

- [agr\_id](executor_events.gettingresults.md#agr_id)
- [task\_id](executor_events.gettingresults.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.gettingresults.md#extract_exc_info)

## Constructors

### constructor

\+ **new GettingResults**(`__namedParameters`: *Object*): [*GettingResults*](executor_events.gettingresults.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*GettingResults*](executor_events.gettingresults.md)

Defined in: [yajsapi/executor/events.ts:280](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L280)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

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
