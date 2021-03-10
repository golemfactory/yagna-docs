# Class: Activity

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [props](../modules/props.md) / Activity

## Class: Activity

[props](../modules/props.md).Activity

### Hierarchy

* [_Model_](props_base.model.md)

  ↳ **Activity**

### Table of contents

#### Constructors

* [constructor](props.activity.md#constructor)

#### Properties

* [cost\_cap](props.activity.md#cost_cap)
* [cost\_warning](props.activity.md#cost_warning)
* [expiration](props.activity.md#expiration)
* [multi\_activity](props.activity.md#multi_activity)
* [timeout\_secs](props.activity.md#timeout_secs)

#### Methods

* [\_custom\_mapping](props.activity.md#_custom_mapping)
* [fields](props.activity.md#fields)
* [from\_properties](props.activity.md#from_properties)
* [keys](props.activity.md#keys)

### Constructors

#### constructor

* **new Activity**\(\): [_Activity_](props.activity.md)

**Returns:** [_Activity_](props.activity.md)

Inherited from: [Model](props_base.model.md)

Defined in: [yajsapi/props/base.ts:108](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/base.ts#L108)

### Properties

#### cost\_cap

• **cost\_cap**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/index.ts:26](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/index.ts#L26)

#### cost\_warning

• **cost\_warning**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/index.ts:32](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/index.ts#L32)

#### expiration

• **expiration**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/index.ts:52](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/index.ts#L52)

#### multi\_activity

• **multi\_activity**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/index.ts:56](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/index.ts#L56)

#### timeout\_secs

• **timeout\_secs**: [_Field_](props_base.field.md)

Defined in: [yajsapi/props/index.ts:41](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/props/index.ts#L41)

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

