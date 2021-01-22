[yajsapi](../README.md) / [Exports](../modules.md) / [props/com](../modules/props_com.md) / ComLinear

# Class: ComLinear

[props/com](../modules/props_com.md).ComLinear

## Hierarchy

* [*Com*](props_com.com.md)

  ↳ **ComLinear**

## Table of contents

### Constructors

- [constructor](props_com.comlinear.md#constructor)

### Properties

- [fixed\_price](props_com.comlinear.md#fixed_price)
- [price\_for](props_com.comlinear.md#price_for)
- [price\_model](props_com.comlinear.md#price_model)
- [scheme](props_com.comlinear.md#scheme)

### Methods

- [\_custom\_mapping](props_com.comlinear.md#_custom_mapping)
- [fields](props_com.comlinear.md#fields)
- [from\_properties](props_com.comlinear.md#from_properties)
- [keys](props_com.comlinear.md#keys)

## Constructors

### constructor

\+ **new ComLinear**(): [*ComLinear*](props_com.comlinear.md)

**Returns:** [*ComLinear*](props_com.comlinear.md)

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:104](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L104)

## Properties

### fixed\_price

• **fixed\_price**: *number*

Defined in: [yajsapi/props/com.ts:31](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L31)

___

### price\_for

• **price\_for**: Object

Defined in: [yajsapi/props/com.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L32)

___

### price\_model

• **price\_model**: [*Field*](props_base.field.md)

Inherited from: [Com](props_com.com.md).[price_model](props_com.com.md#price_model)

Defined in: [yajsapi/props/com.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L27)

___

### scheme

• **scheme**: [*Field*](props_base.field.md)

Inherited from: [Com](props_com.com.md).[scheme](props_com.com.md#scheme)

Defined in: [yajsapi/props/com.ts:26](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L26)

## Methods

### \_custom\_mapping

▸ **_custom_mapping**(`props`: *any*, `data`: *any*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`props` | *any* |
`data` | *any* |

**Returns:** *void*

Overrides: [Com](props_com.com.md)

Defined in: [yajsapi/props/com.ts:34](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L34)

___

### fields

▸ **fields**(`cls`: *any*): [*Field*](props_base.field.md)[]

#### Parameters:

Name | Type |
------ | ------ |
`cls` | *any* |

**Returns:** [*Field*](props_base.field.md)[]

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:109](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L109)

___

### from\_properties

▸ **from_properties**(`props`: *object*): *any*

Initialize the model from an object representation.

**`description`** When provided with an object of properties, it will find the matching keys
   within it and fill the model fields with the values from the object.

   It ignores non-matching keys - i.e. doesn't require filtering of the properties'
   object before the model is fed with the data. Thus, several models can be
   initialized from the same object and all models will only load their own data.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`props` | *object* |     |

**Returns:** *any*

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:133](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L133)

___

### keys

▸ **keys**(): *any*

**`example`** 
```js
import { props } from "yajsapi"
const { Field, Model } = props;
export class NodeInfo extends Model {
  name: Field = new Field({ metadata: { key: "golem.node.id.name" } });
  subnet_tag: Field = new Field({
    metadata: { key: "golem.node.debug.subnet" },
  });
}
new NodeInfo().keys().name()
// Output: 'golem.node.id.name'
```

**Returns:** *any*

a mapping between the model's field names and the property keys

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:178](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L178)
