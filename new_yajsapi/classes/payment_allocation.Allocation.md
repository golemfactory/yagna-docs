# Class: Allocation

[payment/allocation](../modules/payment_allocation.md).Allocation

## Table of contents

### Methods

- [create](payment_allocation.Allocation.md#create)
- [getRemainingAmount](payment_allocation.Allocation.md#getremainingamount)
- [getSpentAmount](payment_allocation.Allocation.md#getspentamount)
- [release](payment_allocation.Allocation.md#release)
- [getDemandDecoration](payment_allocation.Allocation.md#getdemanddecoration)

### Properties

- [id](payment_allocation.Allocation.md#id)
- [timestamp](payment_allocation.Allocation.md#timestamp)
- [timeout](payment_allocation.Allocation.md#timeout)
- [address](payment_allocation.Allocation.md#address)
- [paymentPlatform](payment_allocation.Allocation.md#paymentplatform)
- [totalAmount](payment_allocation.Allocation.md#totalamount)

## Methods

### create

▸ `Static` **create**(`options`): `Promise`<[`Allocation`](payment_allocation.Allocation.md)\>

Create allocation

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `options` | [`AllocationOptions`](../interfaces/payment_allocation.AllocationOptions.md) | [AllocationOptions](../interfaces/payment_allocation.AllocationOptions.md) |

#### Returns

`Promise`<[`Allocation`](payment_allocation.Allocation.md)\>

#### Defined in

[yajsapi/payment/allocation.ts:38](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L38)

___

### getRemainingAmount

▸ **getRemainingAmount**(): `Promise`<`string`\>

Returns remaining amount for allocation

#### Returns

`Promise`<`string`\>

amount remaining

#### Defined in

[yajsapi/payment/allocation.ts:94](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L94)

___

### getSpentAmount

▸ **getSpentAmount**(): `Promise`<`string`\>

Returns already spent amount for allocation

#### Returns

`Promise`<`string`\>

spent amount

#### Defined in

[yajsapi/payment/allocation.ts:104](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L104)

___

### release

▸ **release**(): `Promise`<`void`\>

Release allocation

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/payment/allocation.ts:112](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L112)

___

### getDemandDecoration

▸ **getDemandDecoration**(): `Promise`<`MarketDecoration`\>

Returns Market ya-ts-client decoration

#### Returns

`Promise`<`MarketDecoration`\>

MarketDecoration

#### Defined in

[yajsapi/payment/allocation.ts:124](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L124)

## Properties

### id

• `Readonly` **id**: `string`

Allocation ID

#### Defined in

[yajsapi/payment/allocation.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L19)

___

### timestamp

• `Readonly` **timestamp**: `string`

Timestamp of creation

#### Defined in

[yajsapi/payment/allocation.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L21)

___

### timeout

• `Optional` `Readonly` **timeout**: `string`

Timeout

#### Defined in

[yajsapi/payment/allocation.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L23)

___

### address

• `Readonly` **address**: `string`

Address of requestor

#### Defined in

[yajsapi/payment/allocation.ts:25](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L25)

___

### paymentPlatform

• `Readonly` **paymentPlatform**: `string`

Payment platform

#### Defined in

[yajsapi/payment/allocation.ts:27](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L27)

___

### totalAmount

• `Readonly` **totalAmount**: `string`

Total allocation Amount

#### Defined in

[yajsapi/payment/allocation.ts:29](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/allocation.ts#L29)
