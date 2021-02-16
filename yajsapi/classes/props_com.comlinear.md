# Class: ComLinear

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props/com](../modules/props_com.md) / ComLinear

## Class: ComLinear

[props/com](../modules/props_com.md).ComLinear

### Hierarchy

* [_Com_](props_com.com.md)

  ↳ **ComLinear**

### Table of contents

#### Constructors

* [constructor](props_com.comlinear.md#constructor)

#### Properties

* [fixed\_price](props_com.comlinear.md#fixed_price)
* [price\_for](props_com.comlinear.md#price_for)
* [price\_model](props_com.comlinear.md#price_model)
* [scheme](props_com.comlinear.md#scheme)

#### Methods

* [\_custom\_mapping](props_com.comlinear.md#_custom_mapping)
* [fields](props_com.comlinear.md#fields)
* [from\_properties](props_com.comlinear.md#from_properties)
* [keys](props_com.comlinear.md#keys)

### Constructors

#### constructor

+ **new ComLinear**\(\): [_ComLinear_](props_com.comlinear.md)

**Returns:** [_ComLinear_](props_com.comlinear.md)

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:108](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L108)

### Properties

#### fixed\_price

• **fixed\_price**: _number_

Defined in: [yajsapi/props/com.ts:31](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/com.ts#L31)

#### price\_for

• **price\_for**: Object

Defined in: [yajsapi/props/com.ts:32](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/com.ts#L32)

#### price\_model

• **price\_model**: [_Field_](props_base.field.md)

Inherited from: [Com](props_com.com.md).[price\_model](props_com.com.md#price_model)

Defined in: [yajsapi/props/com.ts:27](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/com.ts#L27)

#### scheme

• **scheme**: [_Field_](props_base.field.md)

Inherited from: [Com](props_com.com.md).[scheme](props_com.com.md#scheme)

Defined in: [yajsapi/props/com.ts:26](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/com.ts#L26)

### Methods

#### \_custom\_mapping

▸ **\_custom\_mapping**\(`props`: _any_, `data`: _any_\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | _any_ |
| `data` | _any_ |

**Returns:** _void_

Overrides: [Com](props_com.com.md)

Defined in: [yajsapi/props/com.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/com.ts#L34)

#### fields

▸ **fields**\(`cls`: _any_\): [_Field_](props_base.field.md)\[\]

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cls` | _any_ |

**Returns:** [_Field_](props_base.field.md)\[\]

Inherited from: [Com](props_com.com.md)

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

Inherited from: [Com](props_com.com.md)

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

Inherited from: [Com](props_com.com.md)

Defined in: [yajsapi/props/base.ts:182](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L182)

