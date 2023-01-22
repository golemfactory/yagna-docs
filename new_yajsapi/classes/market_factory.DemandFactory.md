# Class: DemandFactory

[market/factory](../modules/market_factory.md).DemandFactory

DemandFactory

**`Description`**

Use Demand.create instead

## Table of contents

### Constructors

- [constructor](market_factory.DemandFactory.md#constructor)

### Methods

- [create](market_factory.DemandFactory.md#create)

## Constructors

### constructor

• **new DemandFactory**(`taskPackage`, `allocations`, `options?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `taskPackage` | [`Package`](package_package.Package.md) |
| `allocations` | [`Allocation`](payment_allocation.Allocation.md)[] |
| `options?` | [`DemandOptions`](../interfaces/market_demand.DemandOptions.md) |

#### Defined in

[yajsapi/market/factory.ts:15](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/factory.ts#L15)

## Methods

### create

▸ **create**(): `Promise`<[`Demand`](market_demand.Demand.md)\>

#### Returns

`Promise`<[`Demand`](market_demand.Demand.md)\>

#### Defined in

[yajsapi/market/factory.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/factory.ts#L19)
