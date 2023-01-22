# Class: Demand

[market/demand](../modules/market_demand.md).Demand

## Hierarchy

- `EventTarget`

  ↳ **`Demand`**

## Table of contents

### Methods

- [create](market_demand.Demand.md#create)
- [unsubscribe](market_demand.Demand.md#unsubscribe)

### Properties

- [id](market_demand.Demand.md#id)

## Methods

### create

▸ `Static` **create**(`taskPackage`, `allocations`, `options?`): `Promise`<[`Demand`](market_demand.Demand.md)\>

Create demand for given taskPackage

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `taskPackage` | [`Package`](package_package.Package.md) | Package |
| `allocations` | [`Allocation`](payment_allocation.Allocation.md)[] | Allocation |
| `options?` | [`DemandOptions`](../interfaces/market_demand.DemandOptions.md) | [DemandOptions](../interfaces/market_demand.DemandOptions.md) |

#### Returns

`Promise`<[`Demand`](market_demand.Demand.md)\>

Demand

#### Defined in

[yajsapi/market/demand.ts:40](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L40)

___

### unsubscribe

▸ **unsubscribe**(): `Promise`<`void`\>

Unsubscribe demand

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/market/demand.ts:62](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L62)

## Properties

### id

• `Readonly` **id**: `any`

demand ID

#### Defined in

[yajsapi/market/demand.ts:53](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L53)
