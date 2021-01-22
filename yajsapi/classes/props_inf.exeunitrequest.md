[yajsapi](../README.md) / [Exports](../modules.md) / [props/inf](../modules/props_inf.md) / ExeUnitRequest

# Class: ExeUnitRequest

[props/inf](../modules/props_inf.md).ExeUnitRequest

## Hierarchy

* [*Model*](props_base.model.md)

  ↳ **ExeUnitRequest**

  ↳↳ [*VmRequest*](props_inf.vmrequest.md)

## Table of contents

### Constructors

- [constructor](props_inf.exeunitrequest.md#constructor)

### Properties

- [package\_url](props_inf.exeunitrequest.md#package_url)

### Methods

- [\_custom\_mapping](props_inf.exeunitrequest.md#_custom_mapping)
- [fields](props_inf.exeunitrequest.md#fields)
- [from\_properties](props_inf.exeunitrequest.md#from_properties)
- [keys](props_inf.exeunitrequest.md#keys)

## Constructors

### constructor

\+ **new ExeUnitRequest**(`package_url`: *any*): [*ExeUnitRequest*](props_inf.exeunitrequest.md)

#### Parameters:

Name | Type |
------ | ------ |
`package_url` | *any* |

**Returns:** [*ExeUnitRequest*](props_inf.exeunitrequest.md)

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/inf.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/inf.ts#L56)

## Properties

### package\_url

• **package\_url**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/inf.ts:54](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/inf.ts#L54)

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
