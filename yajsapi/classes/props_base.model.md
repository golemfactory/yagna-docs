# Class: Model

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props/base](../modules/props_base.md) / Model

## Class: Model

[props/base](../modules/props_base.md).Model

Base class from which all property models inherit.

**`description`** Provides helper methods to load the property model data from an object and to get a mapping of all the keys available in the given model.

### Hierarchy

* **Model**

  ↳ [Com](props_com.com.md)

  ↳ [NodeInfo](props.nodeinfo.md)

  ↳ [Activity](https://github.com/golemfactory/yagna-docs/tree/abb2f31f5ef821e06caefa059aea3cf92d48531b/yajsapi/classes/props.activity.md)

  ↳ [ExeUnitRequest](props_inf.exeunitrequest.md)

### Table of contents

#### Constructors

* [constructor](props_base.model.md#constructor)

#### Methods

* [\_custom\_mapping](props_base.model.md#_custom_mapping)
* [fields](props_base.model.md#fields)
* [from\_properties](props_base.model.md#from_properties)
* [keys](props_base.model.md#keys)

### Constructors

#### constructor

• **new Model**\(\)

**Defined in**

[yajsapi/props/base.ts:108](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L108)

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

**Defined in**

[yajsapi/props/base.ts:182](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/props/base.ts#L182)

