[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentAccepted

# Class: PaymentAccepted

[executor/events](../modules/executor_events.md).PaymentAccepted

## Hierarchy

* *AgreementEvent*

  ↳ **PaymentAccepted**

## Table of contents

### Constructors

- [constructor](executor_events.paymentaccepted.md#constructor)

### Properties

- [agr\_id](executor_events.paymentaccepted.md#agr_id)
- [amount](executor_events.paymentaccepted.md#amount)
- [inv\_id](executor_events.paymentaccepted.md#inv_id)

### Methods

- [extract\_exc\_info](executor_events.paymentaccepted.md#extract_exc_info)

## Constructors

### constructor

\+ **new PaymentAccepted**(`__namedParameters`: *Object*): [*PaymentAccepted*](executor_events.paymentaccepted.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*PaymentAccepted*](executor_events.paymentaccepted.md)

Defined in: [yajsapi/executor/events.ts:158](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L158)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### amount

• **amount**: *string*

Defined in: [yajsapi/executor/events.ts:158](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L158)

___

### inv\_id

• **inv\_id**: *string*

Defined in: [yajsapi/executor/events.ts:157](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L157)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
