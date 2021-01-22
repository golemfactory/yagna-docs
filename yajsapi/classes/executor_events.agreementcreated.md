[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / AgreementCreated

# Class: AgreementCreated

[executor/events](../modules/executor_events.md).AgreementCreated

## Hierarchy

* *AgreementEvent*

  ↳ **AgreementCreated**

## Table of contents

### Constructors

- [constructor](executor_events.agreementcreated.md#constructor)

### Properties

- [agr\_id](executor_events.agreementcreated.md#agr_id)
- [provider\_id](executor_events.agreementcreated.md#provider_id)

### Methods

- [extract\_exc\_info](executor_events.agreementcreated.md#extract_exc_info)

## Constructors

### constructor

\+ **new AgreementCreated**(`__namedParameters`: *Object*): [*AgreementCreated*](executor_events.agreementcreated.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*AgreementCreated*](executor_events.agreementcreated.md)

Defined in: [yajsapi/executor/events.ts:127](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L127)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### provider\_id

• `Optional` **provider\_id**: *undefined* \| [*NodeInfo*](props.nodeinfo.md)

Defined in: [yajsapi/executor/events.ts:127](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L127)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
