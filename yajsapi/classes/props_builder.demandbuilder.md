[yajsapi](../README.md) / [Exports](../modules.md) / [props/builder](../modules/props_builder.md) / DemandBuilder

# Class: DemandBuilder

[props/builder](../modules/props_builder.md).DemandBuilder

Builds an object of properties and constraints from high-level models.

**`description`** The object represents a Demand object, which is later matched by the new Golem's
 market implementation against Offers coming from providers to find those providers
 who can satisfy the requestor's demand.

**`example`** 
```js
import dayjs from "dayjs"
import { props } from "yajsapi"

dayjs.extend(utc);

const { Activity, DemandBuilder, NodeInfo } = props;
let builder = new DemandBuilder();
builder.add(NodeInfo("testnet", "a node"));
let act = new yp.Activity();
act.expiration.value = dayjs().utc().unix() * 1000;
builder.add(act);
console.log(builder);
// Output:
// {'properties':
//    {'golem.node.id.name': 'a node',
//     'golem.node.debug.subnet': 'testnet',
//     'golem.srv.comp.expiration': 1601655628772},
//  'constraints': []}
```

## Hierarchy

* **DemandBuilder**

## Table of contents

### Constructors

- [constructor](props_builder.demandbuilder.md#constructor)

### Properties

- [\_constraints](props_builder.demandbuilder.md#_constraints)
- [\_properties](props_builder.demandbuilder.md#_properties)

### Methods

- [add](props_builder.demandbuilder.md#add)
- [constraints](props_builder.demandbuilder.md#constraints)
- [ensure](props_builder.demandbuilder.md#ensure)
- [properties](props_builder.demandbuilder.md#properties)
- [subscribe](props_builder.demandbuilder.md#subscribe)

## Constructors

### constructor

\+ **new DemandBuilder**(): [*DemandBuilder*](props_builder.demandbuilder.md)

**Returns:** [*DemandBuilder*](props_builder.demandbuilder.md)

Defined in: [yajsapi/props/builder.ts:35](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L35)

## Properties

### \_constraints

• **\_constraints**: *string*[]

Defined in: [yajsapi/props/builder.ts:35](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L35)

___

### \_properties

• **\_properties**: Object

Defined in: [yajsapi/props/builder.ts:34](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L34)

## Methods

### add

▸ **add**(`m`: *any*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`m` | *any* |

**Returns:** *void*

Defined in: [yajsapi/props/builder.ts:66](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L66)

___

### constraints

▸ **constraints**(): *string*

**Returns:** *string*

Defined in: [yajsapi/props/builder.ts:47](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L47)

___

### ensure

▸ **ensure**(`constraint`: *string*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`constraint` | *string* |

**Returns:** *void*

Defined in: [yajsapi/props/builder.ts:61](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L61)

___

### properties

▸ **properties**(): *object*

**Returns:** *object*

Defined in: [yajsapi/props/builder.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L42)

___

### subscribe

▸ **subscribe**(`market`: [*Market*](rest_market.market.md)): *Promise*<[*Subscription*](rest_market.subscription.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`market` | [*Market*](rest_market.market.md) |

**Returns:** *Promise*<[*Subscription*](rest_market.subscription.md)\>

Defined in: [yajsapi/props/builder.ts:90](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/builder.ts#L90)
