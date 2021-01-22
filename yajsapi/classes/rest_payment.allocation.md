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

Defined in: [yajsapi/rest/payment.ts:51](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L51)

___

### amount

• **amount**: *number*

Defined in: [yajsapi/rest/payment.ts:65](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L65)

___

### expires

• `Optional` **expires**: *undefined* \| Date

Defined in: [yajsapi/rest/payment.ts:74](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L74)

___

### id

• **id**: *string*

Defined in: [yajsapi/rest/payment.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L62)

___

### payment\_address

• `Optional` **payment\_address**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:71](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L71)

___

### payment\_platform

• `Optional` **payment\_platform**: *undefined* \| *string*

Defined in: [yajsapi/rest/payment.ts:68](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L68)

## Methods

### delete

▸ **delete**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/payment.ts:94](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L94)

___

### details

▸ **details**(): *Promise*<*AllocationDetails*\>

**Returns:** *Promise*<*AllocationDetails*\>

Defined in: [yajsapi/rest/payment.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/payment.ts#L77)
