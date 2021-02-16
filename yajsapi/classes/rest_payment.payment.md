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
- [debit\_note](rest_payment.payment.md#debit_note)
- [decorate\_demand](rest_payment.payment.md#decorate_demand)
- [incoming\_debit\_notes](rest_payment.payment.md#incoming_debit_notes)
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

Defined in: [yajsapi/rest/payment.ts:202](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L202)

## Properties

### \_api

• `Private` **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/payment.ts:202](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L202)

## Methods

### accounts

▸ **accounts**(): *AsyncGenerator*<Account, *any*, *unknown*\>

**Returns:** *AsyncGenerator*<Account, *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:278](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L278)

___

### allocation

▸ **allocation**(`allocation_id`: *string*): *Promise*<[*Allocation*](rest_payment.allocation.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`allocation_id` | *string* |

**Returns:** *Promise*<[*Allocation*](rest_payment.allocation.md)\>

Defined in: [yajsapi/rest/payment.ts:257](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L257)

___

### allocations

▸ **allocations**(): *AsyncGenerator*<[*Allocation*](rest_payment.allocation.md), *any*, *unknown*\>

**Returns:** *AsyncGenerator*<[*Allocation*](rest_payment.allocation.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:235](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L235)

___

### debit\_note

▸ **debit_note**(`debit_note_id`: *string*): *Promise*<[*DebitNote*](rest_payment.debitnote.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`debit_note_id` | *string* |

**Returns:** *Promise*<[*DebitNote*](rest_payment.debitnote.md)\>

Defined in: [yajsapi/rest/payment.ts:292](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L292)

___

### decorate\_demand

▸ **decorate_demand**(`ids`: *string*[]): *Promise*<MarketDecoration\>

#### Parameters:

Name | Type |
------ | ------ |
`ids` | *string*[] |

**Returns:** *Promise*<MarketDecoration\>

Defined in: [yajsapi/rest/payment.ts:285](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L285)

___

### incoming\_debit\_notes

▸ **incoming_debit_notes**(`cancellationToken`: *any*): *AsyncGenerator*<[*DebitNote*](rest_payment.debitnote.md), *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`cancellationToken` | *any* |

**Returns:** *AsyncGenerator*<[*DebitNote*](rest_payment.debitnote.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:354](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L354)

___

### incoming\_invoices

▸ **incoming_invoices**(`cancellationToken`: *any*): *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`cancellationToken` | *any* |

**Returns:** *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:315](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L315)

___

### invoice

▸ **invoice**(`invoice_id`: *string*): *Promise*<[*Invoice*](rest_payment.invoice.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`invoice_id` | *string* |

**Returns:** *Promise*<[*Invoice*](rest_payment.invoice.md)\>

Defined in: [yajsapi/rest/payment.ts:308](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L308)

___

### invoices

▸ **invoices**(): *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

**Returns:** *AsyncGenerator*<[*Invoice*](rest_payment.invoice.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/payment.ts:299](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L299)

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

Defined in: [yajsapi/rest/payment.ts:208](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L208)
