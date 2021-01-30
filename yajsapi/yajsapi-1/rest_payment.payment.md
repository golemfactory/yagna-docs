# rest/payment/payment

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/payment](../yajsapi-2/rest_payment.md) / Payment

## Class: Payment

[rest/payment](../yajsapi-2/rest_payment.md).Payment

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
* [decorate\_demand](rest_payment.payment.md#decorate_demand)
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

Defined in: [yajsapi/rest/payment.ts:156](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L156)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/payment.ts:156](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L156)

### Methods

#### accounts

▸ **accounts**\(\): _AsyncGenerator_

**Returns:** _AsyncGenerator_

Defined in: [yajsapi/rest/payment.ts:224](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L224)

#### allocation

▸ **allocation**\(`allocation_id`: _string_\): _Promise_&lt;[_Allocation_](rest_payment.allocation.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `allocation_id` | _string_ |

**Returns:** _Promise_&lt;[_Allocation_](rest_payment.allocation.md)&gt;

Defined in: [yajsapi/rest/payment.ts:207](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L207)

#### allocations

▸ **allocations**\(\): _AsyncGenerator_&lt;[_Allocation_](rest_payment.allocation.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Allocation_](rest_payment.allocation.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:189](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L189)

#### decorate\_demand

▸ **decorate\_demand**\(`ids`: _string_\[\]\): _Promise_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `ids` | _string_\[\] |

**Returns:** _Promise_

Defined in: [yajsapi/rest/payment.ts:231](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L231)

#### incoming\_invoices

▸ **incoming\_invoices**\(`cancellationToken`: _any_\): _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cancellationToken` | _any_ |

**Returns:** _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:254](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L254)

#### invoice

▸ **invoice**\(`invoice_id`: _string_\): _Promise_&lt;[_Invoice_](rest_payment.invoice.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `invoice_id` | _string_ |

**Returns:** _Promise_&lt;[_Invoice_](rest_payment.invoice.md)&gt;

Defined in: [yajsapi/rest/payment.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L247)

#### invoices

▸ **invoices**\(\): _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Invoice_](rest_payment.invoice.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/payment.ts:238](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L238)

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

Defined in: [yajsapi/rest/payment.ts:162](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L162)

