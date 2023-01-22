# Class: PaymentConfig

[payment/config](../modules/payment_config.md).PaymentConfig

## Hierarchy

- `BaseConfig`

  ↳ **`PaymentConfig`**

## Table of contents

### Constructors

- [constructor](payment_config.PaymentConfig.md#constructor)

### Properties

- [invoiceFetchingInterval](payment_config.PaymentConfig.md#invoicefetchinginterval)
- [debitNotesFetchingInterval](payment_config.PaymentConfig.md#debitnotesfetchinginterval)
- [payingInterval](payment_config.PaymentConfig.md#payinginterval)
- [maxInvoiceEvents](payment_config.PaymentConfig.md#maxinvoiceevents)
- [maxDebitNotesEvents](payment_config.PaymentConfig.md#maxdebitnotesevents)
- [yagnaOptions](payment_config.PaymentConfig.md#yagnaoptions)
- [paymentTimeout](payment_config.PaymentConfig.md#paymenttimeout)
- [api](payment_config.PaymentConfig.md#api)
- [logger](payment_config.PaymentConfig.md#logger)
- [eventTarget](payment_config.PaymentConfig.md#eventtarget)
- [payment](payment_config.PaymentConfig.md#payment)
- [paymentRequestTimeout](payment_config.PaymentConfig.md#paymentrequesttimeout)
- [options](payment_config.PaymentConfig.md#options)

## Constructors

### constructor

• **new PaymentConfig**(`options?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `options?` | [`PaymentOptions`](../interfaces/payment_service.PaymentOptions.md) |

#### Overrides

BaseConfig.constructor

#### Defined in

[yajsapi/payment/config.ts:69](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L69)

## Properties

### invoiceFetchingInterval

• `Readonly` **invoiceFetchingInterval**: `number`

#### Defined in

[yajsapi/payment/config.ts:63](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L63)

___

### debitNotesFetchingInterval

• `Readonly` **debitNotesFetchingInterval**: `number`

#### Defined in

[yajsapi/payment/config.ts:64](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L64)

___

### payingInterval

• `Readonly` **payingInterval**: `number`

#### Defined in

[yajsapi/payment/config.ts:65](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L65)

___

### maxInvoiceEvents

• `Readonly` **maxInvoiceEvents**: `number`

#### Defined in

[yajsapi/payment/config.ts:66](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L66)

___

### maxDebitNotesEvents

• `Readonly` **maxDebitNotesEvents**: `number`

#### Defined in

[yajsapi/payment/config.ts:67](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L67)

___

### yagnaOptions

• `Optional` `Readonly` **yagnaOptions**: [`YagnaOptions`](../modules/executor_executor.md#yagnaoptions)

#### Inherited from

BaseConfig.yagnaOptions

#### Defined in

[yajsapi/payment/config.ts:36](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L36)

___

### paymentTimeout

• `Readonly` **paymentTimeout**: `number`

#### Inherited from

BaseConfig.paymentTimeout

#### Defined in

[yajsapi/payment/config.ts:37](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L37)

___

### api

• `Readonly` **api**: `RequestorApi`

#### Inherited from

BaseConfig.api

#### Defined in

[yajsapi/payment/config.ts:38](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L38)

___

### logger

• `Optional` `Readonly` **logger**: [`Logger`](../interfaces/utils_logger.Logger.md)

#### Inherited from

BaseConfig.logger

#### Defined in

[yajsapi/payment/config.ts:39](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L39)

___

### eventTarget

• `Optional` `Readonly` **eventTarget**: `EventTarget`

#### Inherited from

BaseConfig.eventTarget

#### Defined in

[yajsapi/payment/config.ts:40](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L40)

___

### payment

• `Readonly` **payment**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `driver` | `string` |
| `network` | `string` |

#### Inherited from

BaseConfig.payment

#### Defined in

[yajsapi/payment/config.ts:41](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L41)

___

### paymentRequestTimeout

• `Readonly` **paymentRequestTimeout**: `number`

#### Inherited from

BaseConfig.paymentRequestTimeout

#### Defined in

[yajsapi/payment/config.ts:42](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L42)

___

### options

• `Optional` `Readonly` **options**: [`BasePaymentOptions`](../interfaces/payment_config.BasePaymentOptions.md)

#### Inherited from

BaseConfig.options

#### Defined in

[yajsapi/payment/config.ts:44](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L44)
