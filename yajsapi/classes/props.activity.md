[yajsapi](../README.md) / [Exports](../modules.md) / [props](../modules/props.md) / Activity

# Class: Activity

[props](../modules/props.md).Activity

## Hierarchy

* [*Model*](props_base.model.md)

  ↳ **Activity**

## Table of contents

### Constructors

- [constructor](props.activity.md#constructor)

### Properties

- [cost\_cap](props.activity.md#cost_cap)
- [cost\_warning](props.activity.md#cost_warning)
- [expiration](props.activity.md#expiration)
- [multi\_activity](props.activity.md#multi_activity)
- [timeout\_secs](props.activity.md#timeout_secs)

### Methods

- [\_custom\_mapping](props.activity.md#_custom_mapping)
- [fields](props.activity.md#fields)
- [from\_properties](props.activity.md#from_properties)
- [keys](props.activity.md#keys)

## Constructors

### constructor

\+ **new Activity**(): [*Activity*](props.activity.md)

**Returns:** [*Activity*](props.activity.md)

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:104](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L104)

## Properties

### cost\_cap

• **cost\_cap**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/index.ts:26](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/index.ts#L26)

___

### cost\_warning

• **cost\_warning**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/index.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/index.ts#L32)

___

### expiration

• **expiration**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/index.ts:52](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/index.ts#L52)

___

### multi\_activity

• **multi\_activity**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/index.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/index.ts#L56)

___

### timeout\_secs

• **timeout\_secs**: [*Field*](props_base.field.md)

Defined in: [yajsapi/props/index.ts:41](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/index.ts#L41)

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
