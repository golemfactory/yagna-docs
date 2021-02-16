# Class: Payment

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / Payment

## Class: Payment

[rest/payment](../modules/rest_payment.md).Payment

### Hierarchy

* **Payment**

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

+ **new Payment**\(`cfg`: _Configuration_\): [_Payment_](rest_payment.payment.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cfg` | _Configuration_ |

**Returns:** [_Payment_](rest_payment.payment.md)

Defined in: [yajsapi/rest/payment.ts:202](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L202)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/payment.ts:202](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L202)

### Methods

#### accounts

▸ **accounts**\(\): _AsyncGenerator_

**Returns:** _AsyncGenerator_

Defined in: [yajsapi/rest/payment.ts:278](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L278)

#### allocation

▸ **allocation**\(`allocation_id`: _string_\): _Promise_&lt;[_Allocation_](rest_payment.allocation.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `allocation_id` | _string_ |

**Returns:** _Promise_&lt;[_Allocation_](rest_payment.allocation.md)&gt;

Defined in: [yajsapi/rest/payment.ts:257](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L257)

#### allocations

▸ **allocations**\(\): _AsyncGenerator_&lt;[_Allocation_](rest_payment.allocation.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Allocation_](rest_payment.allocation.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:235](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L235)

#### debit\_note

▸ **debit\_note**\(`debit_note_id`: _string_\): _Promise_&lt;[_DebitNote_](rest_payment.debitnote.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `debit_note_id` | _string_ |

**Returns:** _Promise_&lt;[_DebitNote_](rest_payment.debitnote.md)&gt;

Defined in: [yajsapi/rest/payment.ts:292](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L292)

#### decorate\_demand

▸ **decorate\_demand**\(`ids`: _string_\[\]\): _Promise_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `ids` | _string_\[\] |

**Returns:** _Promise_

Defined in: [yajsapi/rest/payment.ts:285](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L285)

#### incoming\_debit\_notes

▸ **incoming\_debit\_notes**\(`cancellationToken`: _any_\): _AsyncGenerator_&lt;[_DebitNote_](rest_payment.debitnote.md), _any_, _unknown_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cancellationToken` | _any_ |

**Returns:** _AsyncGenerator_&lt;[_DebitNote_](rest_payment.debitnote.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:354](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L354)

#### incoming\_invoices

▸ **incoming\_invoices**\(`cancellationToken`: _any_\): _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cancellationToken` | _any_ |

**Returns:** _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:315](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L315)

#### invoice

▸ **invoice**\(`invoice_id`: _string_\): _Promise_&lt;[_Invoice_](rest_payment.invoice.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `invoice_id` | _string_ |

**Returns:** _Promise_&lt;[_Invoice_](rest_payment.invoice.md)&gt;

Defined in: [yajsapi/rest/payment.ts:308](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L308)

#### invoices

▸ **invoices**\(\): _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:299](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L299)

#### new\_allocation

▸ **new\_allocation**\(`amount`: _number_, `payment_platform`: _string_, `payment_address`: _string_, `expires?`: _null_ \| Date, `make_deposit?`: _boolean_\): [_ResourceCtx_](rest_resource.resourcectx.md)&lt;[_Allocation_](rest_payment.allocation.md)&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `amount` | _number_ | - |
| `payment_platform` | _string_ | - |
| `payment_address` | _string_ | - |
| `expires` | _null_ \| Date | null |
| `make_deposit` | _boolean_ | false |

**Returns:** [_ResourceCtx_](rest_resource.resourcectx.md)&lt;[_Allocation_](rest_payment.allocation.md)&gt;

Defined in: [yajsapi/rest/payment.ts:208](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L208)

