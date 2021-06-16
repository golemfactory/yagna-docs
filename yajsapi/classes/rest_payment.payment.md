[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / Payment

# Class: Payment

[rest/payment](../modules/rest_payment.md).Payment

## Table of contents

### Constructors

- [constructor](rest_payment.payment.md#constructor)

### Properties

- [\_api](rest_payment.payment.md#_api)

### Methods

- [accounts](rest_payment.payment.md#accounts)
- [allocation](rest_payment.payment.md#allocation)
- [allocations](rest_payment.payment.md#allocations)
- [debit\_note](rest_payment.payment.md#debit_note)
- [decorate\_demand](rest_payment.payment.md#decorate_demand)
- [incoming\_debit\_notes](rest_payment.payment.md#incoming_debit_notes)
- [incoming\_invoices](rest_payment.payment.md#incoming_invoices)
- [invoice](rest_payment.payment.md#invoice)
- [invoices](rest_payment.payment.md#invoices)
- [new\_allocation](rest_payment.payment.md#new_allocation)

## Constructors

### constructor

• **new Payment**(`cfg`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `cfg` | `Configuration` |

#### Defined in

[yajsapi/rest/payment.ts:205](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L205)

## Properties

### \_api

• `Private` **\_api**: `RequestorApi`

#### Defined in

[yajsapi/rest/payment.ts:205](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L205)

## Methods

### accounts

▸ **accounts**(): `AsyncGenerator`<Account, any, unknown\>

#### Returns

`AsyncGenerator`<Account, any, unknown\>

#### Defined in

[yajsapi/rest/payment.ts:281](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L281)

___

### allocation

▸ **allocation**(`allocation_id`): `Promise`<[Allocation](rest_payment.allocation.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `allocation_id` | `string` |

#### Returns

`Promise`<[Allocation](rest_payment.allocation.md)\>

#### Defined in

[yajsapi/rest/payment.ts:260](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L260)

___

### allocations

▸ **allocations**(): `AsyncGenerator`<[Allocation](rest_payment.allocation.md), any, unknown\>

#### Returns

`AsyncGenerator`<[Allocation](rest_payment.allocation.md), any, unknown\>

#### Defined in

[yajsapi/rest/payment.ts:238](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L238)

___

### debit\_note

▸ **debit_note**(`debit_note_id`): `Promise`<[DebitNote](rest_payment.debitnote.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `debit_note_id` | `string` |

#### Returns

`Promise`<[DebitNote](rest_payment.debitnote.md)\>

#### Defined in

[yajsapi/rest/payment.ts:295](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L295)

___

### decorate\_demand

▸ **decorate_demand**(`ids`): `Promise`<MarketDecoration\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `ids` | `string`[] |

#### Returns

`Promise`<MarketDecoration\>

#### Defined in

[yajsapi/rest/payment.ts:288](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L288)

___

### incoming\_debit\_notes

▸ **incoming_debit_notes**(`cancellationToken`): `AsyncGenerator`<[DebitNote](rest_payment.debitnote.md), any, unknown\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `cancellationToken` | `any` |

#### Returns

`AsyncGenerator`<[DebitNote](rest_payment.debitnote.md), any, unknown\>

#### Defined in

[yajsapi/rest/payment.ts:359](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L359)

___

### incoming\_invoices

▸ **incoming_invoices**(`cancellationToken`): `AsyncGenerator`<[Invoice](rest_payment.invoice.md), any, unknown\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `cancellationToken` | `any` |

#### Returns

`AsyncGenerator`<[Invoice](rest_payment.invoice.md), any, unknown\>

#### Defined in

[yajsapi/rest/payment.ts:321](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L321)

___

### invoice

▸ **invoice**(`invoice_id`): `Promise`<[Invoice](rest_payment.invoice.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `invoice_id` | `string` |

#### Returns

`Promise`<[Invoice](rest_payment.invoice.md)\>

#### Defined in

[yajsapi/rest/payment.ts:313](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L313)

___

### invoices

▸ **invoices**(): `AsyncGenerator`<[Invoice](rest_payment.invoice.md), any, unknown\>

#### Returns

`AsyncGenerator`<[Invoice](rest_payment.invoice.md), any, unknown\>

#### Defined in

[yajsapi/rest/payment.ts:304](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L304)

___

### new\_allocation

▸ **new_allocation**(`amount`, `payment_platform`, `payment_address`, `expires?`, `make_deposit?`): [ResourceCtx](rest_resource.resourcectx.md)<[Allocation](rest_payment.allocation.md)\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `amount` | `number` | `undefined` |
| `payment_platform` | `string` | `undefined` |
| `payment_address` | `string` | `undefined` |
| `expires` | ``null`` \| `Date` | null |
| `make_deposit` | `boolean` | false |

#### Returns

[ResourceCtx](rest_resource.resourcectx.md)<[Allocation](rest_payment.allocation.md)\>

#### Defined in

[yajsapi/rest/payment.ts:211](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L211)
