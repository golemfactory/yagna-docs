# Class: default

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [utils/queue](../modules/utils_queue.md) / default

## Class: default

[utils/queue](../modules/utils_queue.md).default

### Type parameters

| Name |
| :--- |
| `T` |

### Hierarchy

* **default**

### Table of contents

#### Constructors

* [constructor](utils_queue.default.md#constructor)

#### Properties

* [\_\_new\_items](utils_queue.default.md#__new_items)
* [\_tasks](utils_queue.default.md#_tasks)

#### Methods

* [close](utils_queue.default.md#close)
* [empty](utils_queue.default.md#empty)
* [get](utils_queue.default.md#get)
* [put](utils_queue.default.md#put)

### Constructors

#### constructor

+ **new default**\(`list?`: _never_\[\]\): [_default_](utils_queue.default.md)

**Type parameters:**

| Name |
| :--- |
| `T` |

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `list` | _never_\[\] | ... |

**Returns:** [_default_](utils_queue.default.md)

Defined in: [yajsapi/utils/queue.ts:7](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L7)

### Properties

#### \_\_new\_items

• `Private` **\_\_new\_items**: _any_

Defined in: [yajsapi/utils/queue.ts:7](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L7)

#### \_tasks

• `Private` **\_tasks**: _any_

Defined in: [yajsapi/utils/queue.ts:6](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L6)

### Methods

#### close

▸ **close**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/utils/queue.ts:42](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L42)

#### empty

▸ **empty**\(\): _boolean_

**Returns:** _boolean_

Defined in: [yajsapi/utils/queue.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L38)

#### get

▸ **get**\(\): _Promise_

**Returns:** _Promise_

Defined in: [yajsapi/utils/queue.ts:25](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L25)

#### put

▸ **put**\(`item`: T\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `item` | T |

**Returns:** _void_

Defined in: [yajsapi/utils/queue.ts:19](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/utils/queue.ts#L19)

