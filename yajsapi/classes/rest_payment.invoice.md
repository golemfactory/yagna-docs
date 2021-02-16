# Class: Invoice

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / Invoice

## Class: Invoice

[rest/payment](../modules/rest_payment.md).Invoice

### Hierarchy

* _yInvoice_

  ↳ **Invoice**

### Table of contents

#### Constructors

* [constructor](rest_payment.invoice.md#constructor)

#### Properties

* [\_api](rest_payment.invoice.md#_api)
* [activityIds](rest_payment.invoice.md#activityids)
* [agreementId](rest_payment.invoice.md#agreementid)
* [amount](rest_payment.invoice.md#amount)
* [invoiceId](rest_payment.invoice.md#invoiceid)
* [issuerId](rest_payment.invoice.md#issuerid)
* [lastDebitNoteId](rest_payment.invoice.md#lastdebitnoteid)
* [payeeAddr](rest_payment.invoice.md#payeeaddr)
* [payerAddr](rest_payment.invoice.md#payeraddr)
* [paymentDueDate](rest_payment.invoice.md#paymentduedate)
* [paymentPlatform](rest_payment.invoice.md#paymentplatform)
* [recipientId](rest_payment.invoice.md#recipientid)
* [status](rest_payment.invoice.md#status)
* [timestamp](rest_payment.invoice.md#timestamp)

#### Methods

* [accept](rest_payment.invoice.md#accept)

### Constructors

#### constructor

+ **new Invoice**\(`_api`: _RequestorApi_, `_base`: Invoice\): [_Invoice_](rest_payment.invoice.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `_api` | _RequestorApi_ |
| `_base` | Invoice |

**Returns:** [_Invoice_](rest_payment.invoice.md)

Defined in: [yajsapi/rest/payment.ts:45](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L45)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/payment.ts:45](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L45)

#### activityIds

• `Optional` **activityIds**: _undefined_ \| _string_\[\]

Defined in: [yajsapi/rest/payment.ts:21](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L21)

#### agreementId

• **agreementId**: _string_

Defined in: [yajsapi/rest/payment.ts:20](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L20)

#### amount

• **amount**: _string_

Defined in: [yajsapi/rest/payment.ts:22](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L22)

#### invoiceId

• **invoiceId**: _string_

Defined in: [yajsapi/rest/payment.ts:12](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L12)

#### issuerId

• **issuerId**: _string_

Defined in: [yajsapi/rest/payment.ts:13](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L13)

#### lastDebitNoteId

• `Optional` **lastDebitNoteId**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:18](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L18)

#### payeeAddr

• `Optional` **payeeAddr**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:15](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L15)

#### payerAddr

• `Optional` **payerAddr**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:16](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L16)

#### paymentDueDate

• **paymentDueDate**: _string_

Defined in: [yajsapi/rest/payment.ts:23](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L23)

#### paymentPlatform

• `Optional` **paymentPlatform**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L17)

#### recipientId

• **recipientId**: _string_

Defined in: [yajsapi/rest/payment.ts:14](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L14)

#### status

• **status**: InvoiceStatus

Defined in: [yajsapi/rest/payment.ts:24](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L24)

#### timestamp

• **timestamp**: _string_

Defined in: [yajsapi/rest/payment.ts:19](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L19)

### Methods

#### accept

▸ **accept**\(`amount`: _string_ \| _number_, `allocation`: [_Allocation_](rest_payment.allocation.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `amount` | _string_ \| _number_ |
| `allocation` | [_Allocation_](rest_payment.allocation.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/payment.ts:54](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L54)

