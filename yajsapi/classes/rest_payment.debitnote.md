# Class: DebitNote

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / DebitNote

## Class: DebitNote

[rest/payment](../modules/rest_payment.md).DebitNote

### Hierarchy

* `yDebitNote`

  ↳ **DebitNote**

### Table of contents

#### Constructors

* [constructor](rest_payment.debitnote.md#constructor)

#### Properties

* [\_api](rest_payment.debitnote.md#_api)
* [activityId](rest_payment.debitnote.md#activityid)
* [agreementId](rest_payment.debitnote.md#agreementid)
* [debitNoteId](rest_payment.debitnote.md#debitnoteid)
* [issuerId](rest_payment.debitnote.md#issuerid)
* [payeeAddr](rest_payment.debitnote.md#payeeaddr)
* [payerAddr](rest_payment.debitnote.md#payeraddr)
* [paymentDueDate](rest_payment.debitnote.md#paymentduedate)
* [paymentPlatform](rest_payment.debitnote.md#paymentplatform)
* [previousDebitNoteId](rest_payment.debitnote.md#previousdebitnoteid)
* [recipientId](rest_payment.debitnote.md#recipientid)
* [status](rest_payment.debitnote.md#status)
* [timestamp](rest_payment.debitnote.md#timestamp)
* [totalAmountDue](rest_payment.debitnote.md#totalamountdue)
* [usageCounterVector](rest_payment.debitnote.md#usagecountervector)

#### Methods

* [accept](rest_payment.debitnote.md#accept)

### Constructors

#### constructor

• **new DebitNote**\(`_api`, `_base`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `_api` | `RequestorApi` |
| `_base` | `DebitNote` |

**Overrides**

yDebitNote.constructor

**Defined in**

[yajsapi/rest/payment.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L71)

### Properties

#### \_api

• `Private` **\_api**: `RequestorApi`

**Defined in**

[yajsapi/rest/payment.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L71)

#### activityId

• **activityId**: `string`

**Inherited from**

yDebitNote.activityId

**Defined in**

[yajsapi/rest/payment.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L38)

#### agreementId

• **agreementId**: `string`

**Inherited from**

yDebitNote.agreementId

**Defined in**

[yajsapi/rest/payment.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L37)

#### debitNoteId

• **debitNoteId**: `string`

**Inherited from**

yDebitNote.debitNoteId

**Defined in**

[yajsapi/rest/payment.ts:29](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L29)

#### issuerId

• **issuerId**: `string`

**Inherited from**

yDebitNote.issuerId

**Defined in**

[yajsapi/rest/payment.ts:30](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L30)

#### payeeAddr

• `Optional` **payeeAddr**: `string`

**Inherited from**

yDebitNote.payeeAddr

**Defined in**

[yajsapi/rest/payment.ts:32](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L32)

#### payerAddr

• `Optional` **payerAddr**: `string`

**Inherited from**

yDebitNote.payerAddr

**Defined in**

[yajsapi/rest/payment.ts:33](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L33)

#### paymentDueDate

• `Optional` **paymentDueDate**: `string`

**Inherited from**

yDebitNote.paymentDueDate

**Defined in**

[yajsapi/rest/payment.ts:41](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L41)

#### paymentPlatform

• `Optional` **paymentPlatform**: `string`

**Inherited from**

yDebitNote.paymentPlatform

**Defined in**

[yajsapi/rest/payment.ts:34](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L34)

#### previousDebitNoteId

• `Optional` **previousDebitNoteId**: `string`

**Inherited from**

yDebitNote.previousDebitNoteId

**Defined in**

[yajsapi/rest/payment.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L35)

#### recipientId

• **recipientId**: `string`

**Inherited from**

yDebitNote.recipientId

**Defined in**

[yajsapi/rest/payment.ts:31](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L31)

#### status

• **status**: `InvoiceStatus`

**Inherited from**

yDebitNote.status

**Defined in**

[yajsapi/rest/payment.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L42)

#### timestamp

• **timestamp**: `string`

**Inherited from**

yDebitNote.timestamp

**Defined in**

[yajsapi/rest/payment.ts:36](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L36)

#### totalAmountDue

• **totalAmountDue**: `string`

**Inherited from**

yDebitNote.totalAmountDue

**Defined in**

[yajsapi/rest/payment.ts:39](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L39)

#### usageCounterVector

• `Optional` **usageCounterVector**: `object`

**Inherited from**

yDebitNote.usageCounterVector

**Defined in**

[yajsapi/rest/payment.ts:40](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L40)

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

[yajsapi/rest/payment.ts:80](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L80)

