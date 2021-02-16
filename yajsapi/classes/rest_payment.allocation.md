# Class: Allocation

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/payment](../modules/rest_payment.md) / Allocation

## Class: Allocation

[rest/payment](../modules/rest_payment.md).Allocation

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

Defined in: [yajsapi/rest/payment.ts:89](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L89)

#### amount

• **amount**: _number_

Defined in: [yajsapi/rest/payment.ts:103](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L103)

#### expires

• `Optional` **expires**: _undefined_ \| Date

Defined in: [yajsapi/rest/payment.ts:112](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L112)

#### id

• **id**: _string_

Defined in: [yajsapi/rest/payment.ts:100](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L100)

#### payment\_address

• `Optional` **payment\_address**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:109](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L109)

#### payment\_platform

• `Optional` **payment\_platform**: _undefined_ \| _string_

Defined in: [yajsapi/rest/payment.ts:106](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L106)

### Methods

#### delete

▸ **delete**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/payment.ts:132](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L132)

#### details

▸ **details**\(\): _Promise_&lt;_AllocationDetails_&gt;

**Returns:** _Promise_&lt;_AllocationDetails_&gt;

Defined in: [yajsapi/rest/payment.ts:115](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L115)

