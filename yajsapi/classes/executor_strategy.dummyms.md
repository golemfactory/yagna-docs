# Class: DummyMS

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / DummyMS

## Class: DummyMS

[executor/strategy](../modules/executor_strategy.md).DummyMS

### Hierarchy

* `MarketGeneral`

  ↳ **DummyMS**

### Table of contents

#### Constructors

* [constructor](executor_strategy.dummyms.md#constructor)

#### Properties

* [\_activity](executor_strategy.dummyms.md#_activity)
* [constructor](executor_strategy.dummyms.md#constructor)
* [max\_fixed](executor_strategy.dummyms.md#max_fixed)
* [max\_for\_counter](executor_strategy.dummyms.md#max_for_counter)

#### Methods

* [decorate\_demand](executor_strategy.dummyms.md#decorate_demand)
* [hasOwnProperty](executor_strategy.dummyms.md#hasownproperty)
* [isPrototypeOf](executor_strategy.dummyms.md#isprototypeof)
* [propertyIsEnumerable](executor_strategy.dummyms.md#propertyisenumerable)
* [score\_offer](executor_strategy.dummyms.md#score_offer)
* [toLocaleString](executor_strategy.dummyms.md#tolocalestring)
* [toString](executor_strategy.dummyms.md#tostring)
* [valueOf](executor_strategy.dummyms.md#valueof)

### Constructors

#### constructor

• **new DummyMS**\(\)

**Inherited from**

MarketGeneral.constructor

### Properties

#### \_activity

• `Optional` **\_activity**: [Activity](https://github.com/golemfactory/yagna-docs/tree/abb2f31f5ef821e06caefa059aea3cf92d48531b/yajsapi/classes/props.activity.md)

**Defined in**

[yajsapi/executor/strategy.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L42)

#### constructor

• **constructor**: `Function`

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

**Inherited from**

MarketGeneral.constructor

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:122

#### max\_fixed

• **max\_fixed**: `Number`

**Defined in**

[yajsapi/executor/strategy.ts:41](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L41)

#### max\_for\_counter

• **max\_for\_counter**: `Map`&lt;[Counter](../enumeration/props_com.counter.md), Number&gt;

**Defined in**

[yajsapi/executor/strategy.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L37)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `demand` | [DemandBuilder](props_builder.demandbuilder.md) |

**Returns**

`Promise`

**Overrides**

MarketGeneral.decorate\_demand

**Defined in**

[yajsapi/executor/strategy.ts:44](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L44)

#### hasOwnProperty

▸ **hasOwnProperty**\(`v`\): `boolean`

Determines whether an object has a property with the specified name.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | `string` \| `number` \| `symbol` | A property name. |

**Returns**

`boolean`

**Inherited from**

MarketGeneral.hasOwnProperty

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:137

#### isPrototypeOf

▸ **isPrototypeOf**\(`v`\): `boolean`

Determines whether an object exists in another object's prototype chain.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | `Object` | Another object whose prototype chain is to be checked. |

**Returns**

`boolean`

**Inherited from**

MarketGeneral.isPrototypeOf

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:143

#### propertyIsEnumerable

▸ **propertyIsEnumerable**\(`v`\): `boolean`

Determines whether a specified property is enumerable.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | `string` \| `number` \| `symbol` | A property name. |

**Returns**

`boolean`

**Inherited from**

MarketGeneral.propertyIsEnumerable

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:149

#### score\_offer

▸ **score\_offer**\(`offer`, `history?`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `offer` | [OfferProposal](rest_market.offerproposal.md) |
| `history?` | [ComputationHistory](../interfaces/executor_strategy.computationhistory.md) |

**Returns**

`Promise`

**Overrides**

MarketGeneral.score\_offer

**Defined in**

[yajsapi/executor/strategy.ts:49](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L49)

#### toLocaleString

▸ **toLocaleString**\(\): `string`

Returns a date converted to a string using the current locale.

**Returns**

`string`

**Inherited from**

MarketGeneral.toLocaleString

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:128

#### toString

▸ **toString**\(\): `string`

Returns a string representation of an object.

**Returns**

`string`

**Inherited from**

MarketGeneral.toString

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:125

#### valueOf

▸ **valueOf**\(\): `Object`

Returns the primitive value of the specified object.

**Returns**

`Object`

**Inherited from**

MarketGeneral.valueOf

**Defined in**

node\_modules/typescript/lib/lib.es5.d.ts:131

