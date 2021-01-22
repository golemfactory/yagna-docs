[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / Invoice

# Class: Invoice

[rest/payment](../modules/rest_payment.md).Invoice

## Hierarchy

* *yInvoice*

  ↳ **Invoice**

## Table of contents

### Constructors

- [constructor](rest_payment.invoice.md#constructor)

### Properties

- [\_api](rest_payment.invoice.md#_api)
- [activityIds](rest_payment.invoice.md#activityids)
- [agreementId](rest_payment.invoice.md#agreementid)
- [amount](rest_payment.invoice.md#amount)
- [invoiceId](rest_payment.invoice.md#invoiceid)
- [issuerId](rest_payment.invoice.md#issuerid)
- [lastDebitNoteId](rest_payment.invoice.md#lastdebitnoteid)
- [payeeAddr](rest_payment.invoice.md#payeeaddr)
- [payerAddr](rest_payment.invoice.md#payeraddr)
- [paymentDueDate](rest_payment.invoice.md#paymentduedate)
- [paymentPlatform](rest_payment.invoice.md#paymentplatform)
- [recipientId](rest_payment.invoice.md#recipientid)
- [status](rest_payment.invoice.md#status)
- [timestamp](rest_payment.invoice.md#timestamp)

### Methods

- [accept](rest_payment.invoice.md#accept)

## Constructors

### constructor

\+ **new Invoice**(`_api`: *RequestorApi*, `_base`: Invoice): [*Invoice*](rest_payment.invoice.md)

#### Parameters:

Name | Type |
------ | ------ |
`_api` | *RequestorApi* |
`_base` | Invoice |

**Returns:** [*Invoice*](rest_payment.invoice.md)

Defined in: [yajsapi/rest/payment.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L28)

## Properties

### \_api

• `Private` **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/payment.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L28)

___

### activityIds

• `Optional` **activityIds**: *undefined* \| *string*[]

Defined in: [yajsapi/rest/payment.ts:21](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L21)

___

### agreementId

• **agreementId**: *string*

Defined in: [yajsapi/rest/payment.ts:20](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L20)

___

### amount

• **amount**: *string*

Defined in: [yajsapi/rest/payment.ts:22](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L22)

___

### invoiceId

• **invoiceId**: *string*

Defined in: [yajsapi/rest/payment.ts:12](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L12)

___

### issuerId

• **issuerId**: *string*

Defined in: [yajsapi/rest/payment.ts:13](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L13)

___

### lastDebitNoteId

• `Optional` **lastDebitNoteId**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:18](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L18)

___

### payeeAddr

• `Optional` **payeeAddr**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:15](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L15)

___

### payerAddr

• `Optional` **payerAddr**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:16](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L16)

___

### paymentDueDate

• **paymentDueDate**: *string*

Defined in: [yajsapi/rest/payment.ts:23](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L23)

___

### paymentPlatform

• `Optional` **paymentPlatform**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L17)

___

### recipientId

• **recipientId**: *string*

Defined in: [yajsapi/rest/payment.ts:14](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L14)

___

### status

• **status**: InvoiceStatus

Defined in: [yajsapi/rest/payment.ts:24](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L24)

___

### timestamp

• **timestamp**: *string*

Defined in: [yajsapi/rest/payment.ts:19](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L19)

## Methods

### accept

▸ **accept**(`amount`: *string* \| *number*, `allocation`: [*Allocation*](rest_payment.allocation.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`amount` | *string* \| *number* |
`allocation` | [*Allocation*](rest_payment.allocation.md) |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/payment.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L37)
