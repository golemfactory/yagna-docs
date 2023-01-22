# Class: DebitNote

[payment/debit_note](../modules/payment_debit_note.md).DebitNote

## Hierarchy

- [`BaseNote`](payment_invoice.BaseNote.md)<`Model`\>

  ↳ **`DebitNote`**

## Table of contents

### Methods

- [create](payment_debit_note.DebitNote.md#create)
- [accept](payment_debit_note.DebitNote.md#accept)
- [reject](payment_debit_note.DebitNote.md#reject)
- [refreshStatus](payment_debit_note.DebitNote.md#refreshstatus)
- [getStatus](payment_debit_note.DebitNote.md#getstatus)

### Properties

- [id](payment_debit_note.DebitNote.md#id)
- [previousDebitNoteId](payment_debit_note.DebitNote.md#previousdebitnoteid)
- [timestamp](payment_debit_note.DebitNote.md#timestamp)
- [activityId](payment_debit_note.DebitNote.md#activityid)
- [totalAmountDue](payment_debit_note.DebitNote.md#totalamountdue)
- [usageCounterVector](payment_debit_note.DebitNote.md#usagecountervector)
- [options](payment_debit_note.DebitNote.md#options)
- [providerId](payment_debit_note.DebitNote.md#providerid)
- [recipientId](payment_debit_note.DebitNote.md#recipientid)
- [payeeAddr](payment_debit_note.DebitNote.md#payeeaddr)
- [payerAddr](payment_debit_note.DebitNote.md#payeraddr)
- [paymentPlatform](payment_debit_note.DebitNote.md#paymentplatform)
- [agreementId](payment_debit_note.DebitNote.md#agreementid)
- [paymentDueDate](payment_debit_note.DebitNote.md#paymentduedate)
- [status](payment_debit_note.DebitNote.md#status)

## Methods

### create

▸ `Static` **create**(`debitNoteId`, `options?`): `Promise`<[`DebitNote`](payment_debit_note.DebitNote.md)\>

Create Debit Note Model

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `debitNoteId` | `string` | debit note id |
| `options?` | [`BasePaymentOptions`](../interfaces/payment_config.BasePaymentOptions.md) | [InvoiceOptions](../modules/payment_debit_note.md#invoiceoptions) |

#### Returns

`Promise`<[`DebitNote`](payment_debit_note.DebitNote.md)\>

#### Defined in

[yajsapi/payment/debit_note.ts:26](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L26)

___

### accept

▸ **accept**(`totalAmountAccepted`, `allocationId`): `Promise`<`void`\>

Accept Debit Note

#### Parameters

| Name | Type |
| :------ | :------ |
| `totalAmountAccepted` | `string` |
| `allocationId` | `string` |

#### Returns

`Promise`<`void`\>

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[accept](payment_invoice.BaseNote.md#accept)

#### Defined in

[yajsapi/payment/debit_note.ts:54](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L54)

___

### reject

▸ **reject**(`rejection`): `Promise`<`void`\>

Reject Debit Note

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `rejection` | [`Rejection`](../interfaces/payment_rejection.Rejection.md) | Rejection |

#### Returns

`Promise`<`void`\>

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[reject](payment_invoice.BaseNote.md#reject)

#### Defined in

[yajsapi/payment/debit_note.ts:71](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L71)

___

### refreshStatus

▸ `Protected` **refreshStatus**(): `Promise`<`void`\>

#### Returns

`Promise`<`void`\>

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[refreshStatus](payment_invoice.BaseNote.md#refreshstatus)

#### Defined in

[yajsapi/payment/debit_note.ts:83](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L83)

___

### getStatus

▸ `Protected` **getStatus**(): `Promise`<`InvoiceStatus`\>

#### Returns

`Promise`<`InvoiceStatus`\>

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[getStatus](payment_invoice.BaseNote.md#getstatus)

#### Defined in

[yajsapi/payment/invoice.ts:40](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L40)

## Properties

### id

• `Readonly` **id**: `string`

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[id](payment_invoice.BaseNote.md#id)

#### Defined in

[yajsapi/payment/debit_note.ts:13](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L13)

___

### previousDebitNoteId

• `Optional` `Readonly` **previousDebitNoteId**: `string`

#### Defined in

[yajsapi/payment/debit_note.ts:14](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L14)

___

### timestamp

• `Readonly` **timestamp**: `string`

#### Defined in

[yajsapi/payment/debit_note.ts:15](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L15)

___

### activityId

• `Readonly` **activityId**: `string`

#### Defined in

[yajsapi/payment/debit_note.ts:16](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L16)

___

### totalAmountDue

• `Readonly` **totalAmountDue**: `string`

#### Defined in

[yajsapi/payment/debit_note.ts:17](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L17)

___

### usageCounterVector

• `Optional` `Readonly` **usageCounterVector**: `object`

#### Defined in

[yajsapi/payment/debit_note.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L18)

___

### options

• `Protected` **options**: [`InvoiceConfig`](payment_config.InvoiceConfig.md)

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[options](payment_invoice.BaseNote.md#options)

#### Defined in

[yajsapi/payment/debit_note.ts:39](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/debit_note.ts#L39)

___

### providerId

• `Readonly` **providerId**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[providerId](payment_invoice.BaseNote.md#providerid)

#### Defined in

[yajsapi/payment/invoice.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L21)

___

### recipientId

• `Readonly` **recipientId**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[recipientId](payment_invoice.BaseNote.md#recipientid)

#### Defined in

[yajsapi/payment/invoice.ts:22](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L22)

___

### payeeAddr

• `Readonly` **payeeAddr**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[payeeAddr](payment_invoice.BaseNote.md#payeeaddr)

#### Defined in

[yajsapi/payment/invoice.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L23)

___

### payerAddr

• `Readonly` **payerAddr**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[payerAddr](payment_invoice.BaseNote.md#payeraddr)

#### Defined in

[yajsapi/payment/invoice.ts:24](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L24)

___

### paymentPlatform

• `Readonly` **paymentPlatform**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[paymentPlatform](payment_invoice.BaseNote.md#paymentplatform)

#### Defined in

[yajsapi/payment/invoice.ts:25](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L25)

___

### agreementId

• `Readonly` **agreementId**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[agreementId](payment_invoice.BaseNote.md#agreementid)

#### Defined in

[yajsapi/payment/invoice.ts:26](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L26)

___

### paymentDueDate

• `Optional` `Readonly` **paymentDueDate**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[paymentDueDate](payment_invoice.BaseNote.md#paymentduedate)

#### Defined in

[yajsapi/payment/invoice.ts:27](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L27)

___

### status

• `Protected` **status**: `InvoiceStatus`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[status](payment_invoice.BaseNote.md#status)

#### Defined in

[yajsapi/payment/invoice.ts:28](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L28)
