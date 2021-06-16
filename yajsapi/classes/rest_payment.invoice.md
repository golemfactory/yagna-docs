# Class: Invoice

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / Invoice

## Class: Invoice

[rest/payment](../modules/rest_payment.md).Invoice

### Hierarchy

* `yInvoice`

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

• **new Invoice**\(`_api`, `_base`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `_api` | `RequestorApi` |
| `_base` | `Invoice` |

**Overrides**

yInvoice.constructor

**Defined in**

[yajsapi/rest/payment.ts:46](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L46)

### Properties

#### \_api

• `Private` **\_api**: `RequestorApi`

**Defined in**

[yajsapi/rest/payment.ts:46](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L46)

#### activityIds

• `Optional` **activityIds**: `string`\[\]

**Inherited from**

yInvoice.activityIds

**Defined in**

[yajsapi/rest/payment.ts:22](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L22)

#### agreementId

• **agreementId**: `string`

**Inherited from**

yInvoice.agreementId

**Defined in**

[yajsapi/rest/payment.ts:21](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L21)

#### amount

• **amount**: `string`

**Inherited from**

yInvoice.amount

**Defined in**

[yajsapi/rest/payment.ts:23](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L23)

#### invoiceId

• **invoiceId**: `string`

**Inherited from**

yInvoice.invoiceId

**Defined in**

[yajsapi/rest/payment.ts:13](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L13)

#### issuerId

• **issuerId**: `string`

**Inherited from**

yInvoice.issuerId

**Defined in**

[yajsapi/rest/payment.ts:14](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L14)

#### lastDebitNoteId

• `Optional` **lastDebitNoteId**: `string`

**Inherited from**

yInvoice.lastDebitNoteId

**Defined in**

[yajsapi/rest/payment.ts:19](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L19)

#### payeeAddr

• `Optional` **payeeAddr**: `string`

**Inherited from**

yInvoice.payeeAddr

**Defined in**

[yajsapi/rest/payment.ts:16](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L16)

#### payerAddr

• `Optional` **payerAddr**: `string`

**Inherited from**

yInvoice.payerAddr

**Defined in**

[yajsapi/rest/payment.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L17)

#### paymentDueDate

• **paymentDueDate**: `string`

**Inherited from**

yInvoice.paymentDueDate

**Defined in**

[yajsapi/rest/payment.ts:24](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L24)

#### paymentPlatform

• `Optional` **paymentPlatform**: `string`

**Inherited from**

yInvoice.paymentPlatform

**Defined in**

[yajsapi/rest/payment.ts:18](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L18)

#### recipientId

• **recipientId**: `string`

**Inherited from**

yInvoice.recipientId

**Defined in**

[yajsapi/rest/payment.ts:15](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L15)

#### status

• **status**: `InvoiceStatus`

**Inherited from**

yInvoice.status

**Defined in**

[yajsapi/rest/payment.ts:25](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L25)

#### timestamp

• **timestamp**: `string`

**Inherited from**

yInvoice.timestamp

**Defined in**

[yajsapi/rest/payment.ts:20](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L20)

### Methods

#### accept

▸ **accept**\(`amount`, `allocation`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `amount` | `string` \| `number` |
| `allocation` | [Allocation](rest_payment.allocation.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/payment.ts:55](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L55)

