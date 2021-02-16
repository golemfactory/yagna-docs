# Class: ExeUnitRequest

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props/inf](../modules/props_inf.md) / ExeUnitRequest

## Class: ExeUnitRequest

[props/inf](../modules/props_inf.md).ExeUnitRequest

### Hierarchy

* [_Model_](props_base.model.md)

  ↳ **ExeUnitRequest**

  ↳↳ [_VmRequest_](props_inf.vmrequest.md)

### Table of contents

#### Constructors

* [constructor](props_inf.exeunitrequest.md#constructor)

#### Properties

* [package\_url](props_inf.exeunitrequest.md#package_url)

#### Methods

* [\_custom\_mapping](props_inf.exeunitrequest.md#_custom_mapping)
* [fields](props_inf.exeunitrequest.md#fields)
* [from\_properties](props_inf.exeunitrequest.md#from_properties)
* [keys](props_inf.exeunitrequest.md#keys)

### Constructors

#### constructor

+ **new ExeUnitRequest**\(`package_url`: _any_\): [_ExeUnitRequest_](props_inf.exeunitrequest.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `package_url` | _any_ |

**Returns:** [_ExeUnitRequest_](props_inf.exeunitrequest.md)

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/inf.ts:56](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/inf.ts#L56)

### Properties

#### package\_url

• **package\_url**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/inf.ts:54](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/inf.ts#L54)

### Methods

#### \_custom\_mapping

▸ **\_custom\_mapping**\(`props`: _object_, `data`: _object_\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | _object_ |
| `data` | _object_ |

**Returns:** _void_

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:111](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L111)

#### fields

▸ **fields**\(`cls`: _any_\): [_Field_](props_base.field.md)\[\]

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cls` | _any_ |

**Returns:** [_Field_](props_base.field.md)\[\]

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:113](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L113)

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

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:137](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L137)

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

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:182](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L182)

