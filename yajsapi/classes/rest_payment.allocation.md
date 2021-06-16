[yajsapi](../README.md) / [Exports](../modules.md) / [rest/payment](../modules/rest_payment.md) / Allocation

# Class: Allocation

[rest/payment](../modules/rest_payment.md).Allocation

## Hierarchy

- `\_Link`

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

• **new Allocation**()

#### Inherited from

\_Link.constructor

## Properties

### \_api

• **\_api**: `RequestorApi`

#### Inherited from

\_Link.\_api

#### Defined in

[yajsapi/rest/payment.ts:94](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L94)

___

### amount

• **amount**: `number`

#### Defined in

[yajsapi/rest/payment.ts:108](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L108)

___

### expires

• `Optional` **expires**: `Date`

#### Defined in

[yajsapi/rest/payment.ts:117](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L117)

___

### id

• **id**: `string`

#### Defined in

[yajsapi/rest/payment.ts:105](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L105)

___

### payment\_address

• `Optional` **payment\_address**: `string`

#### Defined in

[yajsapi/rest/payment.ts:114](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L114)

___

### payment\_platform

• `Optional` **payment\_platform**: `string`

#### Defined in

[yajsapi/rest/payment.ts:111](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L111)

## Methods

### delete

▸ **delete**(): `Promise`<void\>

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/rest/payment.ts:132](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L132)

___

### details

▸ **details**(): `Promise`<AllocationDetails\>

#### Returns

`Promise`<AllocationDetails\>

#### Defined in

[yajsapi/rest/payment.ts:120](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/payment.ts#L120)
