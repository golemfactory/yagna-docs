[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentFailed

# Class: PaymentFailed

[executor/events](../modules/executor_events.md).PaymentFailed

## Hierarchy

* *AgreementEvent*

  ↳ **PaymentFailed**

## Table of contents

### Constructors

- [constructor](executor_events.paymentfailed.md#constructor)

### Properties

- [agr\_id](executor_events.paymentfailed.md#agr_id)

### Methods

- [extract\_exc\_info](executor_events.paymentfailed.md#extract_exc_info)

## Constructors

### constructor

\+ **new PaymentFailed**(`__namedParameters`: *Object*): [*PaymentFailed*](executor_events.paymentfailed.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*PaymentFailed*](executor_events.paymentfailed.md)

Defined in: [yajsapi/executor/events.ts:167](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L167)

## Properties

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
