# Class: DebitNote

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / DebitNote

## Class: DebitNote

[rest/payment](../modules/rest_payment.md).DebitNote

### Hierarchy

* _yDebitNote_

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

+ **new DebitNote**\(`_api`: _RequestorApi_, `_base`: DebitNote\): [_DebitNote_](rest_payment.debitnote.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `_api` | _RequestorApi_ |
| `_base` | DebitNote |

**Returns:** [_DebitNote_](rest_payment.debitnote.md)

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L68)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L68)

#### activityId

• **activityId**: _string_

Defined in: [yajsapi/rest/payment.ts:37](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L37)

#### agreementId

• **agreementId**: _string_

Defined in: [yajsapi/rest/payment.ts:36](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L36)

#### debitNoteId

• **debitNoteId**: _string_

Defined in: [yajsapi/rest/payment.ts:28](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L28)

#### issuerId

• **issuerId**: _string_

Defined in: [yajsapi/rest/payment.ts:29](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L29)

#### payeeAddr

• `Optional` **payeeAddr**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:31](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L31)

#### payerAddr

• `Optional` **payerAddr**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:32](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L32)

#### paymentDueDate

• `Optional` **paymentDueDate**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:40](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L40)

#### paymentPlatform

• `Optional` **paymentPlatform**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:33](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L33)

#### previousDebitNoteId

• `Optional` **previousDebitNoteId**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L34)

#### recipientId

• **recipientId**: _string_

Defined in: [yajsapi/rest/payment.ts:30](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L30)

#### status

• **status**: InvoiceStatus

Defined in: [yajsapi/rest/payment.ts:41](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L41)

#### timestamp

• **timestamp**: _string_

Defined in: [yajsapi/rest/payment.ts:35](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L35)

#### totalAmountDue

• **totalAmountDue**: _string_

Defined in: [yajsapi/rest/payment.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L38)

#### usageCounterVector

• `Optional` **usageCounterVector**: _undefined_ \| _object_

Defined in: [yajsapi/rest/payment.ts:39](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L39)

### Methods

#### accept

▸ **accept**\(`amount`: _string_ \| _number_, `allocation`: [_Allocation_](rest_payment.allocation.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `amount` | _string_ \| _number_ |
| `allocation` | [_Allocation_](rest_payment.allocation.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/payment.ts:77](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L77)

