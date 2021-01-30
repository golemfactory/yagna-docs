# utils/queue.default

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [utils/queue](../yajsapi-2/utils_queue.md) / default

## Class: default

[utils/queue](../yajsapi-2/utils_queue.md).default

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

* [\_cancellationToken](utils_queue.default.md#_cancellationtoken)
* [\_tasks](utils_queue.default.md#_tasks)

#### Methods

* [empty](utils_queue.default.md#empty)
* [get](utils_queue.default.md#get)
* [put](utils_queue.default.md#put)

### Constructors

#### constructor

+ **new default**\(`list?`: _never_\[\], `cancellationToken`: _any_\): [_default_](utils_queue.default.md)

**Type parameters:**

| Name |
| :--- |
| `T` |

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `list` | _never_\[\] | ... |
| `cancellationToken` | _any_ | - |

**Returns:** [_default_](utils_queue.default.md)

Defined in: [yajsapi/utils/queue.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L5)

### Properties

#### \_cancellationToken

• `Private` **\_cancellationToken**: _any_

Defined in: [yajsapi/utils/queue.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L5)

#### \_tasks

• `Private` **\_tasks**: _any_

Defined in: [yajsapi/utils/queue.ts:4](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L4)

### Methods

#### empty

▸ **empty**\(\): _boolean_

**Returns:** _boolean_

Defined in: [yajsapi/utils/queue.ts:33](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L33)

#### get

▸ **get**\(\): _Promise_

**Returns:** _Promise_

Defined in: [yajsapi/utils/queue.ts:20](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L20)

#### put

▸ **put**\(`item`: T\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `item` | T |

**Returns:** _void_

Defined in: [yajsapi/utils/queue.ts:16](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L16)

