[yajsapi](../README.md) / [Exports](../modules.md) / [props/com](../modules/props_com.md) / Com

# Class: Com

[props/com](../modules/props_com.md).Com

## Hierarchy

* [*Model*](props_base.model.md)

  ↳ **Com**

  ↳↳ [*ComLinear*](props_com.comlinear.md)

## Table of contents

### Constructors

- [constructor](props_com.com.md#constructor)

### Properties

- [price\_model](props_com.com.md#price_model)
- [scheme](props_com.com.md#scheme)

### Methods

- [\_custom\_mapping](props_com.com.md#_custom_mapping)
- [fields](props_com.com.md#fields)
- [from\_properties](props_com.com.md#from_properties)
- [keys](props_com.com.md#keys)

## Constructors

### constructor

\+ **new Com**(): [*Com*](props_com.com.md)

**Returns:** [*Com*](props_com.com.md)

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:104](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L104)

## Properties

### price\_model

• **price\_model**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/com.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L27)

___

### scheme

• **scheme**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/com.ts:26](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/com.ts#L26)

## Methods

### \_custom\_mapping

▸ **_custom_mapping**(`props`: *object*, `data`: *object*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`props` | *object* |
`data` | *object* |

**Returns:** *void*

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:107](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L107)

___

### fields

▸ **fields**(`cls`: *any*): [*Field*](props_base.field.md)[]

#### Parameters:

Name | Type |
------ | ------ |
`cls` | *any* |

**Returns:** [*Field*](props_base.field.md)[]

Inherited from: [Model](props_base.model.md)

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

Inherited from: [Model](props_base.model.md)

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

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:178](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L178)
