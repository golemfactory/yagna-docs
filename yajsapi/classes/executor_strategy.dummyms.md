[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / DummyMS

# Class: DummyMS

[executor/strategy](../modules/executor_strategy.md).DummyMS

## Hierarchy

- `MarketGeneral`

  ↳ **DummyMS**

## Table of contents

### Constructors

- [constructor](executor_strategy.dummyms.md#constructor)

### Properties

- [\_activity](executor_strategy.dummyms.md#_activity)
- [constructor](executor_strategy.dummyms.md#constructor)
- [max\_fixed](executor_strategy.dummyms.md#max_fixed)
- [max\_for\_counter](executor_strategy.dummyms.md#max_for_counter)

### Methods

- [decorate\_demand](executor_strategy.dummyms.md#decorate_demand)
- [hasOwnProperty](executor_strategy.dummyms.md#hasownproperty)
- [isPrototypeOf](executor_strategy.dummyms.md#isprototypeof)
- [propertyIsEnumerable](executor_strategy.dummyms.md#propertyisenumerable)
- [score\_offer](executor_strategy.dummyms.md#score_offer)
- [toLocaleString](executor_strategy.dummyms.md#tolocalestring)
- [toString](executor_strategy.dummyms.md#tostring)
- [valueOf](executor_strategy.dummyms.md#valueof)

## Constructors

### constructor

• **new DummyMS**()

#### Inherited from

MarketGeneral.constructor

## Properties

### \_activity

• `Optional` **\_activity**: [Activity](props.activity.md)

#### Defined in

[yajsapi/executor/strategy.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L42)

___

### constructor

• **constructor**: `Function`

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

#### Inherited from

MarketGeneral.constructor

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:122

___

### max\_fixed

• **max\_fixed**: `Number`

#### Defined in

[yajsapi/executor/strategy.ts:41](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L41)

___

### max\_for\_counter

• **max\_for\_counter**: `Map`<[Counter](../enums/props_com.counter.md), Number\>

#### Defined in

[yajsapi/executor/strategy.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L37)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `demand` | [DemandBuilder](props_builder.demandbuilder.md) |

#### Returns

`Promise`<void\>

#### Overrides

MarketGeneral.decorate\_demand

#### Defined in

[yajsapi/executor/strategy.ts:44](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L44)

___

### hasOwnProperty

▸ **hasOwnProperty**(`v`): `boolean`

Determines whether an object has a property with the specified name.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `v` | `string` \| `number` \| `symbol` | A property name. |

#### Returns

`boolean`

#### Inherited from

MarketGeneral.hasOwnProperty

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:137

___

### isPrototypeOf

▸ **isPrototypeOf**(`v`): `boolean`

Determines whether an object exists in another object's prototype chain.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `v` | `Object` | Another object whose prototype chain is to be checked. |

#### Returns

`boolean`

#### Inherited from

MarketGeneral.isPrototypeOf

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:143

___

### propertyIsEnumerable

▸ **propertyIsEnumerable**(`v`): `boolean`

Determines whether a specified property is enumerable.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `v` | `string` \| `number` \| `symbol` | A property name. |

#### Returns

`boolean`

#### Inherited from

MarketGeneral.propertyIsEnumerable

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:149

___

### score\_offer

▸ **score_offer**(`offer`, `history?`): `Promise`<Number\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `offer` | [OfferProposal](rest_market.offerproposal.md) |
| `history?` | [ComputationHistory](../interfaces/executor_strategy.computationhistory.md) |

#### Returns

`Promise`<Number\>

#### Overrides

MarketGeneral.score\_offer

#### Defined in

[yajsapi/executor/strategy.ts:49](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L49)

___

### toLocaleString

▸ **toLocaleString**(): `string`

Returns a date converted to a string using the current locale.

#### Returns

`string`

#### Inherited from

MarketGeneral.toLocaleString

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:128

___

### toString

▸ **toString**(): `string`

Returns a string representation of an object.

#### Returns

`string`

#### Inherited from

MarketGeneral.toString

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:125

___

### valueOf

▸ **valueOf**(): `Object`

Returns the primitive value of the specified object.

#### Returns

`Object`

#### Inherited from

MarketGeneral.valueOf

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:131
