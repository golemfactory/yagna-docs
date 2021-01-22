[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentQueued

# Class: PaymentQueued

[executor/events](../modules/executor_events.md).PaymentQueued

## Hierarchy

* *AgreementEvent*

  ↳ **PaymentQueued**

## Table of contents

### Constructors

- [constructor](executor_events.paymentqueued.md#constructor)

### Properties

- [agr\_id](executor_events.paymentqueued.md#agr_id)

### Methods

- [extract\_exc\_info](executor_events.paymentqueued.md#extract_exc_info)

## Constructors

### constructor

\+ **new PaymentQueued**(`__namedParameters`: *Object*): [*PaymentQueued*](executor_events.paymentqueued.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*PaymentQueued*](executor_events.paymentqueued.md)

Defined in: [yajsapi/executor/events.ts:182](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L182)

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
