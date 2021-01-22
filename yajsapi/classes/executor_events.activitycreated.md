[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ActivityCreated

# Class: ActivityCreated

[executor/events](../modules/executor_events.md).ActivityCreated

## Hierarchy

* *AgreementEvent*

  ↳ **ActivityCreated**

## Table of contents

### Constructors

- [constructor](executor_events.activitycreated.md#constructor)

### Properties

- [act\_id](executor_events.activitycreated.md#act_id)
- [agr\_id](executor_events.activitycreated.md#agr_id)

### Methods

- [extract\_exc\_info](executor_events.activitycreated.md#extract_exc_info)

## Constructors

### constructor

\+ **new ActivityCreated**(`__namedParameters`: *Object*): [*ActivityCreated*](executor_events.activitycreated.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ActivityCreated*](executor_events.activitycreated.md)

Defined in: [yajsapi/executor/events.ts:211](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L211)

## Properties

### act\_id

• `Optional` **act\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:211](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L211)

___

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
