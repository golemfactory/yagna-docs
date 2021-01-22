[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / Payment

# Class: Payment

[rest/payment](../modules/rest_payment.md).Payment

## Hierarchy

* **Payment**

## Table of contents

### Constructors

- [constructor](rest_payment.payment.md#constructor)

### Properties

- [\_api](rest_payment.payment.md#_api)

### Methods

- [accounts](rest_payment.payment.md#accounts)
- [allocation](rest_payment.payment.md#allocation)
- [allocations](rest_payment.payment.md#allocations)
- [decorate\_demand](rest_payment.payment.md#decorate_demand)
- [incoming\_invoices](rest_payment.payment.md#incoming_invoices)
- [invoice](rest_payment.payment.md#invoice)
- [invoices](rest_payment.payment.md#invoices)
- [new\_allocation](rest_payment.payment.md#new_allocation)

## Constructors

### constructor

\+ **new Payment**(`cfg`: *Configuration*): [*Payment*](rest_payment.payment.md)

#### Parameters:

Name | Type |
------ | ------ |
`cfg` | *Configuration* |

**Returns:** [*Payment*](rest_payment.payment.md)

Defined in: [yajsapi/rest/payment.ts:156](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L156)

## Properties

### \_api

• `Private` **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/payment.ts:156](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L156)

## Methods

### accounts

▸ **accounts**(): *AsyncGenerator*<Account, *any*, *unknown*\>

**Returns:** *AsyncGenerator*<Account, *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:224](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L224)

___

### allocation

▸ **allocation**(`allocation_id`: *string*): *Promise*<[*Allocation*](rest_payment.allocation.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`allocation_id` | *string* |

**Returns:** *Promise*<[*Allocation*](rest_payment.allocation.md)\>

Defined in: [yajsapi/rest/payment.ts:207](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L207)

___

### allocations

▸ **allocations**(): *AsyncGenerator*<[*Allocation*](rest_payment.allocation.md), *any*, *unknown*\>

**Returns:** *AsyncGenerator*<[*Allocation*](rest_payment.allocation.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:189](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L189)

___

### decorate\_demand

▸ **decorate_demand**(`ids`: *string*[]): *Promise*<MarketDecoration\>

#### Parameters:

Name | Type |
------ | ------ |
`ids` | *string*[] |

**Returns:** *Promise*<MarketDecoration\>

Defined in: [yajsapi/rest/payment.ts:231](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L231)

___

### incoming\_invoices

▸ **incoming_invoices**(`cancellationToken`: *any*): *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`cancellationToken` | *any* |

**Returns:** *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:254](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L254)

___

### invoice

▸ **invoice**(`invoice_id`: *string*): *Promise*<[*Invoice*](rest_payment.invoice.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`invoice_id` | *string* |

**Returns:** *Promise*<[*Invoice*](rest_payment.invoice.md)\>

Defined in: [yajsapi/rest/payment.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L247)

___

### invoices

▸ **invoices**(): *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

**Returns:** *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:238](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L238)

___

### new\_allocation

▸ **new_allocation**(`amount`: *number*, `payment_platform`: *string*, `payment_address`: *string*, `expires?`: *null* \| Date, `make_deposit?`: *boolean*): [*ResourceCtx*](rest_resource.resourcectx.md)<[*Allocation*](rest_payment.allocation.md)\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`amount` | *number* | - |
`payment_platform` | *string* | - |
`payment_address` | *string* | - |
`expires` | *null* \| Date | null |
`make_deposit` | *boolean* | false |

**Returns:** [*ResourceCtx*](rest_resource.resourcectx.md)<[*Allocation*](rest_payment.allocation.md)\>

Defined in: [yajsapi/rest/payment.ts:162](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L162)
