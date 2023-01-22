# Class: Invoice

[payment/invoice](../modules/payment_invoice.md).Invoice

## Hierarchy

- [`BaseNote`](payment_invoice.BaseNote.md)<`Model`\>

  ↳ **`Invoice`**

## Table of contents

### Methods

- [create](payment_invoice.Invoice.md#create)
- [getStatus](payment_invoice.Invoice.md#getstatus)
- [accept](payment_invoice.Invoice.md#accept)
- [reject](payment_invoice.Invoice.md#reject)
- [refreshStatus](payment_invoice.Invoice.md#refreshstatus)

### Properties

- [id](payment_invoice.Invoice.md#id)
- [activityIds](payment_invoice.Invoice.md#activityids)
- [amount](payment_invoice.Invoice.md#amount)
- [timestamp](payment_invoice.Invoice.md#timestamp)
- [recipientId](payment_invoice.Invoice.md#recipientid)
- [options](payment_invoice.Invoice.md#options)
- [providerId](payment_invoice.Invoice.md#providerid)
- [payeeAddr](payment_invoice.Invoice.md#payeeaddr)
- [payerAddr](payment_invoice.Invoice.md#payeraddr)
- [paymentPlatform](payment_invoice.Invoice.md#paymentplatform)
- [agreementId](payment_invoice.Invoice.md#agreementid)
- [paymentDueDate](payment_invoice.Invoice.md#paymentduedate)
- [status](payment_invoice.Invoice.md#status)

## Methods

### create

▸ `Static` **create**(`invoiceId`, `options?`): `Promise`<[`Invoice`](payment_invoice.Invoice.md)\>

Create invoice using invoice ID

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `invoiceId` | `string` | Invoice ID |
| `options?` | [`BasePaymentOptions`](../interfaces/payment_config.BasePaymentOptions.md) | [InvoiceOptions](../modules/payment_invoice.md#invoiceoptions) |

#### Returns

`Promise`<[`Invoice`](payment_invoice.Invoice.md)\>

#### Defined in

[yajsapi/payment/invoice.ts:70](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L70)

___

### getStatus

▸ **getStatus**(): `Promise`<`InvoiceStatus`\>

Get Invoice Status

#### Returns

`Promise`<`InvoiceStatus`\>

InvoiceStatus

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[getStatus](payment_invoice.BaseNote.md#getstatus)

#### Defined in

[yajsapi/payment/invoice.ts:97](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L97)

___

### accept

▸ **accept**(`totalAmountAccepted`, `allocationId`): `Promise`<`void`\>

Accept Invoice

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

[yajsapi/payment/invoice.ts:108](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L108)

___

### reject

▸ **reject**(`rejection`): `Promise`<`void`\>

Reject Invoice

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `rejection` | [`Rejection`](../interfaces/payment_rejection.Rejection.md) | Rejection |

#### Returns

`Promise`<`void`\>

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[reject](payment_invoice.BaseNote.md#reject)

#### Defined in

[yajsapi/payment/invoice.ts:126](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L126)

___

### refreshStatus

▸ `Protected` **refreshStatus**(): `Promise`<`void`\>

#### Returns

`Promise`<`void`\>

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[refreshStatus](payment_invoice.BaseNote.md#refreshstatus)

#### Defined in

[yajsapi/payment/invoice.ts:138](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L138)

## Properties

### id

• `Readonly` **id**: `string`

Invoice ID

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[id](payment_invoice.BaseNote.md#id)

#### Defined in

[yajsapi/payment/invoice.ts:54](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L54)

___

### activityIds

• `Optional` `Readonly` **activityIds**: `string`[]

Activities IDs covered by this Invoice

#### Defined in

[yajsapi/payment/invoice.ts:56](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L56)

___

### amount

• `Readonly` **amount**: `string`

Amount in the invoice

#### Defined in

[yajsapi/payment/invoice.ts:58](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L58)

___

### timestamp

• `Readonly` **timestamp**: `string`

Invoice creation timestamp

#### Defined in

[yajsapi/payment/invoice.ts:60](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L60)

___

### recipientId

• `Readonly` **recipientId**: `string`

Recipient ID

#### Overrides

[BaseNote](payment_invoice.BaseNote.md).[recipientId](payment_invoice.BaseNote.md#recipientid)

#### Defined in

[yajsapi/payment/invoice.ts:62](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L62)

___

### options

• `Protected` **options**: [`InvoiceConfig`](payment_config.InvoiceConfig.md)

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[options](payment_invoice.BaseNote.md#options)

#### Defined in

[yajsapi/payment/invoice.ts:83](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L83)

___

### providerId

• `Readonly` **providerId**: `string`

#### Inherited from

[BaseNote](payment_invoice.BaseNote.md).[providerId](payment_invoice.BaseNote.md#providerid)

#### Defined in

[yajsapi/payment/invoice.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/invoice.ts#L21)

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
