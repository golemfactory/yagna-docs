# executor/strategy/dummyms

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/strategy](../yajsapi-2/executor_strategy.md) / DummyMS

## Class: DummyMS

[executor/strategy](../yajsapi-2/executor_strategy.md).DummyMS

### Hierarchy

* _MarketGeneral_

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

+ **new DummyMS**\(\): [_DummyMS_](executor_strategy.dummyms.md)

**Returns:** [_DummyMS_](executor_strategy.dummyms.md)

### Properties

#### \_activity

• `Optional` **\_activity**: _undefined_ \| [_Activity_](props.activity.md)

Defined in: [yajsapi/executor/strategy.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L40)

#### constructor

• **constructor**: Function

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:122

#### max\_fixed

• **max\_fixed**: Number

Defined in: [yajsapi/executor/strategy.ts:39](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L39)

#### max\_for\_counter

• **max\_for\_counter**: _Map_&lt;[_Counter_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/enums/props_com.counter.md), Number&gt;

Defined in: [yajsapi/executor/strategy.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L38)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`: [_DemandBuilder_](props_builder.demandbuilder.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `demand` | [_DemandBuilder_](props_builder.demandbuilder.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/strategy.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L42)

#### hasOwnProperty

▸ **hasOwnProperty**\(`v`: _string_ \| _number_ \| _symbol_\): _boolean_

Determines whether an object has a property with the specified name.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | _string_ \| _number_ \| _symbol_ | A property name. |

**Returns:** _boolean_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:137

#### isPrototypeOf

▸ **isPrototypeOf**\(`v`: Object\): _boolean_

Determines whether an object exists in another object's prototype chain.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | Object | Another object whose prototype chain is to be checked. |

**Returns:** _boolean_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:143

#### propertyIsEnumerable

▸ **propertyIsEnumerable**\(`v`: _string_ \| _number_ \| _symbol_\): _boolean_

Determines whether a specified property is enumerable.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | _string_ \| _number_ \| _symbol_ | A property name. |

**Returns:** _boolean_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:149

#### score\_offer

▸ **score\_offer**\(`offer`: [_OfferProposal_](rest_market.offerproposal.md)\): _Promise_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `offer` | [_OfferProposal_](rest_market.offerproposal.md) |

**Returns:** _Promise_

Defined in: [yajsapi/executor/strategy.ts:47](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L47)

#### toLocaleString

▸ **toLocaleString**\(\): _string_

Returns a date converted to a string using the current locale.

**Returns:** _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:128

#### toString

▸ **toString**\(\): _string_

Returns a string representation of an object.

**Returns:** _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:125

#### valueOf

▸ **valueOf**\(\): Object

Returns the primitive value of the specified object.

**Returns:** Object

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:131

