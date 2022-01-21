# Class: Payment

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / Payment

## Class: Payment

[rest/payment](../modules/rest_payment.md).Payment

### Table of contents

#### Constructors

* [constructor](rest_payment.payment.md#constructor)

#### Properties

* [\_api](rest_payment.payment.md#_api)

#### Methods

* [accounts](rest_payment.payment.md#accounts)
* [allocation](rest_payment.payment.md#allocation)
* [allocations](rest_payment.payment.md#allocations)
* [debit\_note](rest_payment.payment.md#debit_note)
* [decorate\_demand](rest_payment.payment.md#decorate_demand)
* [incoming\_debit\_notes](rest_payment.payment.md#incoming_debit_notes)
* [incoming\_invoices](rest_payment.payment.md#incoming_invoices)
* [invoice](rest_payment.payment.md#invoice)
* [invoices](rest_payment.payment.md#invoices)
* [new\_allocation](rest_payment.payment.md#new_allocation)

### Constructors

#### constructor

• **new Payment**\(`cfg`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `cfg` | `Configuration` |

**Defined in**

[yajsapi/rest/payment.ts:205](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L205)

### Properties

#### \_api

• `Private` **\_api**: `RequestorApi`

**Defined in**

[yajsapi/rest/payment.ts:205](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L205)

### Methods

#### accounts

▸ **accounts**\(\): `AsyncGenerator`

**Returns**

`AsyncGenerator`

**Defined in**

[yajsapi/rest/payment.ts:281](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L281)

#### allocation

▸ **allocation**\(`allocation_id`\): `Promise`&lt;[Allocation](rest_payment.allocation.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `allocation_id` | `string` |

**Returns**

`Promise`&lt;[Allocation](rest_payment.allocation.md)&gt;

**Defined in**

[yajsapi/rest/payment.ts:260](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L260)

#### allocations

▸ **allocations**\(\): `AsyncGenerator`&lt;[Allocation](rest_payment.allocation.md), any, unknown&gt;

**Returns**

`AsyncGenerator`&lt;[Allocation](rest_payment.allocation.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/payment.ts:238](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L238)

#### debit\_note

▸ **debit\_note**\(`debit_note_id`\): `Promise`&lt;[DebitNote](rest_payment.debitnote.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `debit_note_id` | `string` |

**Returns**

`Promise`&lt;[DebitNote](rest_payment.debitnote.md)&gt;

**Defined in**

[yajsapi/rest/payment.ts:295](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L295)

#### decorate\_demand

▸ **decorate\_demand**\(`ids`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `ids` | `string`\[\] |

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/payment.ts:288](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L288)

#### incoming\_debit\_notes

▸ **incoming\_debit\_notes**\(`cancellationToken`\): `AsyncGenerator`&lt;[DebitNote](rest_payment.debitnote.md), any, unknown&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `cancellationToken` | `any` |

**Returns**

`AsyncGenerator`&lt;[DebitNote](rest_payment.debitnote.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/payment.ts:359](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L359)

#### incoming\_invoices

▸ **incoming\_invoices**\(`cancellationToken`\): `AsyncGenerator`&lt;[Invoice](rest_payment.invoice.md), any, unknown&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `cancellationToken` | `any` |

**Returns**

`AsyncGenerator`&lt;[Invoice](rest_payment.invoice.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/payment.ts:321](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L321)

#### invoice

▸ **invoice**\(`invoice_id`\): `Promise`&lt;[Invoice](rest_payment.invoice.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `invoice_id` | `string` |

**Returns**

`Promise`&lt;[Invoice](rest_payment.invoice.md)&gt;

**Defined in**

[yajsapi/rest/payment.ts:313](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L313)

#### invoices

▸ **invoices**\(\): `AsyncGenerator`&lt;[Invoice](rest_payment.invoice.md), any, unknown&gt;

**Returns**

`AsyncGenerator`&lt;[Invoice](rest_payment.invoice.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/payment.ts:304](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L304)

#### new\_allocation

▸ **new\_allocation**\(`amount`, `payment_platform`, `payment_address`, `expires?`, `make_deposit?`\): [ResourceCtx](rest_resource.resourcectx.md)&lt;[Allocation](rest_payment.allocation.md)&gt;

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `amount` | `number` | `undefined` |
| `payment_platform` | `string` | `undefined` |
| `payment_address` | `string` | `undefined` |
| `expires` | `null` \| `Date` | null |
| `make_deposit` | `boolean` | false |

**Returns**

[ResourceCtx](rest_resource.resourcectx.md)&lt;[Allocation](rest_payment.allocation.md)&gt;

**Defined in**

[yajsapi/rest/payment.ts:211](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L211)

