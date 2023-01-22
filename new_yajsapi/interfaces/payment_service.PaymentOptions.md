# Interface: PaymentOptions

[payment/service](../modules/payment_service.md).PaymentOptions

## Hierarchy

- [`BasePaymentOptions`](payment_config.BasePaymentOptions.md)

  ↳ **`PaymentOptions`**

## Table of contents

### Properties

- [invoiceFetchingInterval](payment_service.PaymentOptions.md#invoicefetchinginterval)
- [debitNotesFetchingInterval](payment_service.PaymentOptions.md#debitnotesfetchinginterval)
- [payingInterval](payment_service.PaymentOptions.md#payinginterval)
- [maxInvoiceEvents](payment_service.PaymentOptions.md#maxinvoiceevents)
- [maxDebitNotesEvents](payment_service.PaymentOptions.md#maxdebitnotesevents)
- [yagnaOptions](payment_service.PaymentOptions.md#yagnaoptions)
- [budget](payment_service.PaymentOptions.md#budget)
- [payment](payment_service.PaymentOptions.md#payment)
- [paymentTimeout](payment_service.PaymentOptions.md#paymenttimeout)
- [paymentRequestTimeout](payment_service.PaymentOptions.md#paymentrequesttimeout)
- [logger](payment_service.PaymentOptions.md#logger)
- [eventTarget](payment_service.PaymentOptions.md#eventtarget)

## Properties

### invoiceFetchingInterval

• `Optional` **invoiceFetchingInterval**: `number`

#### Defined in

[yajsapi/payment/service.ts:10](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/service.ts#L10)

___

### debitNotesFetchingInterval

• `Optional` **debitNotesFetchingInterval**: `number`

#### Defined in

[yajsapi/payment/service.ts:11](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/service.ts#L11)

___

### payingInterval

• `Optional` **payingInterval**: `number`

#### Defined in

[yajsapi/payment/service.ts:12](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/service.ts#L12)

___

### maxInvoiceEvents

• `Optional` **maxInvoiceEvents**: `number`

#### Defined in

[yajsapi/payment/service.ts:13](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/service.ts#L13)

___

### maxDebitNotesEvents

• `Optional` **maxDebitNotesEvents**: `number`

#### Defined in

[yajsapi/payment/service.ts:14](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/service.ts#L14)

___

### yagnaOptions

• `Optional` **yagnaOptions**: [`YagnaOptions`](../modules/executor_executor.md#yagnaoptions)

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[yagnaOptions](payment_config.BasePaymentOptions.md#yagnaoptions)

#### Defined in

[yajsapi/payment/config.ts:26](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L26)

___

### budget

• `Optional` **budget**: `number`

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[budget](payment_config.BasePaymentOptions.md#budget)

#### Defined in

[yajsapi/payment/config.ts:27](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L27)

___

### payment

• `Optional` **payment**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `driver?` | `string` |
| `network?` | `string` |

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[payment](payment_config.BasePaymentOptions.md#payment)

#### Defined in

[yajsapi/payment/config.ts:28](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L28)

___

### paymentTimeout

• `Optional` **paymentTimeout**: `number`

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[paymentTimeout](payment_config.BasePaymentOptions.md#paymenttimeout)

#### Defined in

[yajsapi/payment/config.ts:29](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L29)

___

### paymentRequestTimeout

• `Optional` **paymentRequestTimeout**: `number`

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[paymentRequestTimeout](payment_config.BasePaymentOptions.md#paymentrequesttimeout)

#### Defined in

[yajsapi/payment/config.ts:30](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L30)

___

### logger

• `Optional` **logger**: [`Logger`](utils_logger.Logger.md)

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[logger](payment_config.BasePaymentOptions.md#logger)

#### Defined in

[yajsapi/payment/config.ts:31](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L31)

___

### eventTarget

• `Optional` **eventTarget**: `EventTarget`

#### Inherited from

[BasePaymentOptions](payment_config.BasePaymentOptions.md).[eventTarget](payment_config.BasePaymentOptions.md#eventtarget)

#### Defined in

[yajsapi/payment/config.ts:32](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L32)
