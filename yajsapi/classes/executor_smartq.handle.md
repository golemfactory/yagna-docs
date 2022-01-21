# Class: Handle

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/smartq](../modules/executor_smartq.md) / Handle

## Class: Handle

[executor/smartq](../modules/executor_smartq.md).Handle

### Type parameters

| Name |
| :--- |
| `Item` |

### Table of contents

#### Constructors

* [constructor](executor_smartq.handle.md#constructor)

#### Properties

* [\_consumer](executor_smartq.handle.md#_consumer)
* [\_data](executor_smartq.handle.md#_data)
* [\_prev\_consumers](executor_smartq.handle.md#_prev_consumers)

#### Methods

* [assign\_consumer](executor_smartq.handle.md#assign_consumer)
* [consumer](executor_smartq.handle.md#consumer)
* [data](executor_smartq.handle.md#data)

### Constructors

#### constructor

• **new Handle**\(`__namedParameters`\)

**Type parameters**

| Name |
| :--- |
| `Item` |

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Defined in**

[yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L9)

### Properties

#### \_consumer

• `Private` **\_consumer**: `null` \| [Consumer](executor_smartq.consumer.md)

**Defined in**

[yajsapi/executor/smartq.ts:7](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L7)

#### \_data

• `Private` **\_data**: `Item`

**Defined in**

[yajsapi/executor/smartq.ts:8](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L8)

#### \_prev\_consumers

• `Private` **\_prev\_consumers**: `Set`&lt;[Consumer](executor_smartq.consumer.md)&gt;

**Defined in**

[yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L9)

### Methods

#### assign\_consumer

▸ **assign\_consumer**\(`consumer`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `consumer` | [Consumer](executor_smartq.consumer.md) |

**Returns**

`void`

**Defined in**

[yajsapi/executor/smartq.ts:22](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L22)

#### consumer

▸ **consumer**\(\): `null` \| [Consumer](executor_smartq.consumer.md)

**Returns**

`null` \| [Consumer](executor_smartq.consumer.md)

**Defined in**

[yajsapi/executor/smartq.ts:18](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L18)

#### data

▸ **data**\(\): `Item`

**Returns**

`Item`

**Defined in**

[yajsapi/executor/smartq.ts:27](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L27)

