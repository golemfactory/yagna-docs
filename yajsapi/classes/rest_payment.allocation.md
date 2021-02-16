[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / Allocation

# Class: Allocation

[rest/payment](../modules/rest_payment.md).Allocation

## Hierarchy

* *\_Link*

  ↳ **Allocation**

## Table of contents

### Constructors

- [constructor](rest_payment.allocation.md#constructor)

### Properties

- [\_api](rest_payment.allocation.md#_api)
- [amount](rest_payment.allocation.md#amount)
- [expires](rest_payment.allocation.md#expires)
- [id](rest_payment.allocation.md#id)
- [payment\_address](rest_payment.allocation.md#payment_address)
- [payment\_platform](rest_payment.allocation.md#payment_platform)

### Methods

- [delete](rest_payment.allocation.md#delete)
- [details](rest_payment.allocation.md#details)

## Constructors

### constructor

\+ **new Allocation**(): [*Allocation*](rest_payment.allocation.md)

**Returns:** [*Allocation*](rest_payment.allocation.md)

## Properties

### \_api

• **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/payment.ts:89](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L89)

___

### amount

• **amount**: *number*

Defined in: [yajsapi/rest/payment.ts:103](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L103)

___

### expires

• `Optional` **expires**: *undefined* \| Date

Defined in: [yajsapi/rest/payment.ts:112](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L112)

___

### id

• **id**: *string*

Defined in: [yajsapi/rest/payment.ts:100](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L100)

___

### payment\_address

• `Optional` **payment\_address**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:109](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L109)

___

### payment\_platform

• `Optional` **payment\_platform**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:106](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L106)

## Methods

### delete

▸ **delete**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/payment.ts:132](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L132)

___

### details

▸ **details**(): *Promise*<*AllocationDetails*\>

**Returns:** *Promise*<*AllocationDetails*\>

Defined in: [yajsapi/rest/payment.ts:115](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/payment.ts#L115)
