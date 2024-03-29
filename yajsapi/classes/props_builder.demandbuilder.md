# Class: DemandBuilder

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props/builder](../modules/props_builder.md) / DemandBuilder

## Class: DemandBuilder

[props/builder](../modules/props_builder.md).DemandBuilder

Builds an object of properties and constraints from high-level models.

**`description`** The object represents a Demand object, which is later matched by the new Golem's market implementation against Offers coming from providers to find those providers who can satisfy the requestor's demand.

**`example`**

```javascript
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

### Table of contents

#### Constructors

* [constructor](props_builder.demandbuilder.md#constructor)

#### Properties

* [\_constraints](props_builder.demandbuilder.md#_constraints)
* [\_properties](props_builder.demandbuilder.md#_properties)

#### Methods

* [add](props_builder.demandbuilder.md#add)
* [constraints](props_builder.demandbuilder.md#constraints)
* [ensure](props_builder.demandbuilder.md#ensure)
* [properties](props_builder.demandbuilder.md#properties)
* [subscribe](props_builder.demandbuilder.md#subscribe)

### Constructors

#### constructor

• **new DemandBuilder**\(\)

**Defined in**

[yajsapi/props/builder.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L35)

### Properties

#### \_constraints

• **\_constraints**: `string`\[\]

**Defined in**

[yajsapi/props/builder.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L35)

#### \_properties

• **\_properties**: `Object`

**Defined in**

[yajsapi/props/builder.ts:34](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L34)

### Methods

#### add

▸ **add**\(`m`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `m` | `any` |

**Returns**

`void`

**Defined in**

[yajsapi/props/builder.ts:66](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L66)

#### constraints

▸ **constraints**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/props/builder.ts:47](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L47)

#### ensure

▸ **ensure**\(`constraint`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `constraint` | `string` |

**Returns**

`void`

**Defined in**

[yajsapi/props/builder.ts:61](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L61)

#### properties

▸ **properties**\(\): `object`

**Returns**

`object`

**Defined in**

[yajsapi/props/builder.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L42)

#### subscribe

▸ **subscribe**\(`market`\): `Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `market` | [Market](rest_market.market.md) |

**Returns**

`Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Defined in**

[yajsapi/props/builder.ts:90](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/builder.ts#L90)

