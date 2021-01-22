[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / DummyMS

# Class: DummyMS

[executor/strategy](../modules/executor_strategy.md).DummyMS

## Hierarchy

* *MarketGeneral*

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

\+ **new DummyMS**(): [*DummyMS*](executor_strategy.dummyms.md)

**Returns:** [*DummyMS*](executor_strategy.dummyms.md)

## Properties

### \_activity

• `Optional` **\_activity**: *undefined* \| [*Activity*](props.activity.md)

Defined in: [yajsapi/executor/strategy.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L40)

___

### constructor

• **constructor**: Function

The initial value of Object.prototype.constructor is the standard built-in Object constructor.

Defined in: node_modules/typescript/lib/lib.es5.d.ts:122

___

### max\_fixed

• **max\_fixed**: Number

Defined in: [yajsapi/executor/strategy.ts:39](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L39)

___

### max\_for\_counter

• **max\_for\_counter**: *Map*<[*Counter*](../enums/props_com.counter.md), Number\>

Defined in: [yajsapi/executor/strategy.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L38)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`: [*DemandBuilder*](props_builder.demandbuilder.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`demand` | [*DemandBuilder*](props_builder.demandbuilder.md) |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/strategy.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L42)

___

### hasOwnProperty

▸ **hasOwnProperty**(`v`: *string* \| *number* \| *symbol*): *boolean*

Determines whether an object has a property with the specified name.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`v` | *string* \| *number* \| *symbol* | A property name.    |

**Returns:** *boolean*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:137

___

### isPrototypeOf

▸ **isPrototypeOf**(`v`: Object): *boolean*

Determines whether an object exists in another object's prototype chain.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`v` | Object | Another object whose prototype chain is to be checked.    |

**Returns:** *boolean*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:143

___

### propertyIsEnumerable

▸ **propertyIsEnumerable**(`v`: *string* \| *number* \| *symbol*): *boolean*

Determines whether a specified property is enumerable.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`v` | *string* \| *number* \| *symbol* | A property name.    |

**Returns:** *boolean*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:149

___

### score\_offer

▸ **score_offer**(`offer`: [*OfferProposal*](rest_market.offerproposal.md)): *Promise*<Number\>

#### Parameters:

Name | Type |
------ | ------ |
`offer` | [*OfferProposal*](rest_market.offerproposal.md) |

**Returns:** *Promise*<Number\>

Defined in: [yajsapi/executor/strategy.ts:47](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L47)

___

### toLocaleString

▸ **toLocaleString**(): *string*

Returns a date converted to a string using the current locale.

**Returns:** *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:128

___

### toString

▸ **toString**(): *string*

Returns a string representation of an object.

**Returns:** *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:125

___

### valueOf

▸ **valueOf**(): Object

Returns the primitive value of the specified object.

**Returns:** Object

Defined in: node_modules/typescript/lib/lib.es5.d.ts:131
