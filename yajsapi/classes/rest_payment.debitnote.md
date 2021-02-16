[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / DebitNote

# Class: DebitNote

[rest/payment](../modules/rest_payment.md).DebitNote

## Hierarchy

* *yDebitNote*

  ↳ **DebitNote**

## Table of contents

### Constructors

- [constructor](rest_payment.debitnote.md#constructor)

### Properties

- [\_api](rest_payment.debitnote.md#_api)
- [activityId](rest_payment.debitnote.md#activityid)
- [agreementId](rest_payment.debitnote.md#agreementid)
- [debitNoteId](rest_payment.debitnote.md#debitnoteid)
- [issuerId](rest_payment.debitnote.md#issuerid)
- [payeeAddr](rest_payment.debitnote.md#payeeaddr)
- [payerAddr](rest_payment.debitnote.md#payeraddr)
- [paymentDueDate](rest_payment.debitnote.md#paymentduedate)
- [paymentPlatform](rest_payment.debitnote.md#paymentplatform)
- [previousDebitNoteId](rest_payment.debitnote.md#previousdebitnoteid)
- [recipientId](rest_payment.debitnote.md#recipientid)
- [status](rest_payment.debitnote.md#status)
- [timestamp](rest_payment.debitnote.md#timestamp)
- [totalAmountDue](rest_payment.debitnote.md#totalamountdue)
- [usageCounterVector](rest_payment.debitnote.md#usagecountervector)

### Methods

- [accept](rest_payment.debitnote.md#accept)

## Constructors

### constructor

\+ **new DebitNote**(`_api`: *RequestorApi*, `_base`: DebitNote): [*DebitNote*](rest_payment.debitnote.md)

#### Parameters:

Name | Type |
------ | ------ |
`_api` | *RequestorApi* |
`_base` | DebitNote |

**Returns:** [*DebitNote*](rest_payment.debitnote.md)

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L68)

## Properties

### \_api

• `Private` **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L68)

___

### activityId

• **activityId**: *string*

Defined in: [yajsapi/rest/payment.ts:37](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L37)

___

### agreementId

• **agreementId**: *string*

Defined in: [yajsapi/rest/payment.ts:36](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L36)

___

### debitNoteId

• **debitNoteId**: *string*

Defined in: [yajsapi/rest/payment.ts:28](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L28)

___

### issuerId

• **issuerId**: *string*

Defined in: [yajsapi/rest/payment.ts:29](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L29)

___

### payeeAddr

• `Optional` **payeeAddr**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:31](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L31)

___

### payerAddr

• `Optional` **payerAddr**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:32](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L32)

___

### paymentDueDate

• `Optional` **paymentDueDate**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:40](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L40)

___

### paymentPlatform

• `Optional` **paymentPlatform**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:33](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L33)

___

### previousDebitNoteId

• `Optional` **previousDebitNoteId**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L34)

___

### recipientId

• **recipientId**: *string*

Defined in: [yajsapi/rest/payment.ts:30](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L30)

___

### status

• **status**: InvoiceStatus

Defined in: [yajsapi/rest/payment.ts:41](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L41)

___

### timestamp

• **timestamp**: *string*

Defined in: [yajsapi/rest/payment.ts:35](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L35)

___

### totalAmountDue

• **totalAmountDue**: *string*

Defined in: [yajsapi/rest/payment.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L38)

___

### usageCounterVector

• `Optional` **usageCounterVector**: *undefined* \| *object*

Defined in: [yajsapi/rest/payment.ts:39](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L39)

## Methods

### accept

▸ **accept**(`amount`: *string* \| *number*, `allocation`: [*Allocation*](rest_payment.allocation.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`amount` | *string* \| *number* |
`allocation` | [*Allocation*](rest_payment.allocation.md) |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/payment.ts:77](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L77)
