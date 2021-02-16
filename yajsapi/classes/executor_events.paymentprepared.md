[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentPrepared

# Class: PaymentPrepared

[executor/events](../modules/executor_events.md).PaymentPrepared

## Hierarchy

* *AgreementEvent*

  ↳ **PaymentPrepared**

## Table of contents

### Constructors

- [constructor](executor_events.paymentprepared.md#constructor)

### Properties

- [agr\_id](executor_events.paymentprepared.md#agr_id)

### Methods

- [extract\_exc\_info](executor_events.paymentprepared.md#extract_exc_info)

## Constructors

### constructor

\+ **new PaymentPrepared**(`__namedParameters`: *Object*): [*PaymentPrepared*](executor_events.paymentprepared.md)

#### Parameters:

• **__namedParameters**: *Object*

**Returns:** [*PaymentPrepared*](executor_events.paymentprepared.md)

Defined in: [yajsapi/executor/events.ts:190](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L190)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)
