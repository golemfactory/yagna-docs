# Class: NodeInfo

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props](../modules/props.md) / NodeInfo

## Class: NodeInfo

[props](../modules/props.md).NodeInfo

### Hierarchy

* [Model](props_base.model.md)

  ↳ **NodeInfo**

### Table of contents

#### Constructors

* [constructor](props.nodeinfo.md#constructor)

#### Properties

* [name](props.nodeinfo.md#name)
* [subnet\_tag](props.nodeinfo.md#subnet_tag)

#### Methods

* [\_custom\_mapping](props.nodeinfo.md#_custom_mapping)
* [fields](props.nodeinfo.md#fields)
* [from\_properties](props.nodeinfo.md#from_properties)
* [keys](props.nodeinfo.md#keys)

### Constructors

#### constructor

• **new NodeInfo**\(`subnet_tag?`, `name?`\)

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `subnet_tag` | `string` | "testnet" |
| `name?` | `string` | `undefined` |

**Overrides**

[Model](props_base.model.md).[constructor](props_base.model.md#constructor)

**Defined in**

[yajsapi/props/index.ts:10](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/index.ts#L10)

### Properties

#### name

• **name**: [Field](props_base.field.md)

**Defined in**

[yajsapi/props/index.ts:7](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/index.ts#L7)

#### subnet\_tag

• **subnet\_tag**: [Field](props_base.field.md)

**Defined in**

[yajsapi/props/index.ts:8](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/index.ts#L8)

### Methods

#### \_custom\_mapping

▸ **\_custom\_mapping**\(`props`, `data`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `props` | `object` |
| `data` | `object` |

**Returns**

`void`

**Inherited from**

[Model](props_base.model.md).[\_custom\_mapping](props_base.model.md#_custom_mapping)

**Defined in**

[yajsapi/props/base.ts:111](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L111)

#### fields

▸ **fields**\(`cls`\): [Field](props_base.field.md)\[\]

**Parameters**

| Name | Type |
| :--- | :--- |
| `cls` | `any` |

**Returns**

[Field](props_base.field.md)\[\]

**Inherited from**

[Model](props_base.model.md).[fields](props_base.model.md#fields)

**Defined in**

[yajsapi/props/base.ts:113](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L113)

#### from\_properties

▸ **from\_properties**\(`props`\): `any`

Initialize the model from an object representation.

**`description`** When provided with an object of properties, it will find the matching keys within it and fill the model fields with the values from the object.

It ignores non-matching keys - i.e. doesn't require filtering of the properties' object before the model is fed with the data. Thus, several models can be initialized from the same object and all models will only load their own data.

**Parameters**

| Name | Type |
| :--- | :--- |
| `props` | `object` |

**Returns**

`any`

**Inherited from**

[Model](props_base.model.md).[from\_properties](props_base.model.md#from_properties)

**Defined in**

[yajsapi/props/base.ts:137](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L137)

#### keys

▸ **keys**\(\): `any`

**`example`**

```javascript
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

**Returns**

`any`

a mapping between the model's field names and the property keys

**Inherited from**

[Model](props_base.model.md).[keys](props_base.model.md#keys)

**Defined in**

[yajsapi/props/base.ts:182](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L182)

