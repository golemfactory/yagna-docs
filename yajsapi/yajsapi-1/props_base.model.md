# props/base/model

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [props/base](../yajsapi-2/props_base.md) / Model

## Class: Model

[props/base](../yajsapi-2/props_base.md).Model

Base class from which all property models inherit.

**`description`** Provides helper methods to load the property model data from an object and to get a mapping of all the keys available in the given model.

### Hierarchy

* **Model**

  ↳ [_Com_](props_com.com.md)

  ↳ [_NodeInfo_](props.nodeinfo.md)

  ↳ [_Activity_](props.activity.md)

  ↳ [_ExeUnitRequest_](props_inf.exeunitrequest.md)

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

+ **new Model**\(\): [_Model_](props_base.model.md)

**Returns:** [_Model_](props_base.model.md)

Defined in: [yajsapi/props/base.ts:104](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L104)

### Methods

#### \_custom\_mapping

▸ **\_custom\_mapping**\(`props`: _object_, `data`: _object_\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | _object_ |
| `data` | _object_ |

**Returns:** _void_

Defined in: [yajsapi/props/base.ts:107](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L107)

#### fields

▸ **fields**\(`cls`: _any_\): [_Field_](props_base.field.md)\[\]

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cls` | _any_ |

**Returns:** [_Field_](props_base.field.md)\[\]

Defined in: [yajsapi/props/base.ts:109](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L109)

#### from\_properties

▸ **from\_properties**\(`props`: _object_\): _any_

Initialize the model from an object representation.

**`description`** When provided with an object of properties, it will find the matching keys within it and fill the model fields with the values from the object.

It ignores non-matching keys - i.e. doesn't require filtering of the properties' object before the model is fed with the data. Thus, several models can be initialized from the same object and all models will only load their own data.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `props` | _object_ |  |

**Returns:** _any_

Defined in: [yajsapi/props/base.ts:133](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L133)

#### keys

▸ **keys**\(\): _any_

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

**Returns:** _any_

a mapping between the model's field names and the property keys

Defined in: [yajsapi/props/base.ts:178](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/props/base.ts#L178)

