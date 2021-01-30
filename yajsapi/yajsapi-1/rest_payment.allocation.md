# rest/payment/allocation

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/payment](../yajsapi-2/rest_payment.md) / Allocation

## Class: Allocation

[rest/payment](../yajsapi-2/rest_payment.md).Allocation

### Hierarchy

* _\_Link_

  ↳ **Allocation**

### Table of contents

#### Constructors

* [constructor](rest_payment.allocation.md#constructor)

#### Properties

* [\_api](rest_payment.allocation.md#_api)
* [amount](rest_payment.allocation.md#amount)
* [expires](rest_payment.allocation.md#expires)
* [id](rest_payment.allocation.md#id)
* [payment\_address](rest_payment.allocation.md#payment_address)
* [payment\_platform](rest_payment.allocation.md#payment_platform)

#### Methods

* [delete](rest_payment.allocation.md#delete)
* [details](rest_payment.allocation.md#details)

### Constructors

#### constructor

+ **new Allocation**\(\): [_Allocation_](rest_payment.allocation.md)

**Returns:** [_Allocation_](rest_payment.allocation.md)

### Properties

#### \_api

• **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/payment.ts:51](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L51)

#### amount

• **amount**: _number_

Defined in: [yajsapi/rest/payment.ts:65](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L65)

#### expires

• `Optional` **expires**: _undefined_ \| Date

Defined in: [yajsapi/rest/payment.ts:74](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L74)

#### id

• **id**: _string_

Defined in: [yajsapi/rest/payment.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L62)

#### payment\_address

• `Optional` **payment\_address**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:71](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L71)

#### payment\_platform

• `Optional` **payment\_platform**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L68)

### Methods

#### delete

▸ **delete**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/payment.ts:94](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L94)

#### details

▸ **details**\(\): _Promise_&lt;_AllocationDetails_&gt;

**Returns:** _Promise_&lt;_AllocationDetails_&gt;

Defined in: [yajsapi/rest/payment.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L77)

