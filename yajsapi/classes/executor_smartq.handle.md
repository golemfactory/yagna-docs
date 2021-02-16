# Class: Handle

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/smartq](../modules/executor_smartq.md) / Handle

## Class: Handle

[executor/smartq](../modules/executor_smartq.md).Handle

### Type parameters

| Name |
| :--- |
| `Item` |

### Hierarchy

* **Handle**

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

+ **new Handle**\(`__namedParameters`: _Object_\): [_Handle_](executor_smartq.handle.md)

**Type parameters:**

| Name |
| :--- |
| `Item` |

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_Handle_](executor_smartq.handle.md)

Defined in: [yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L9)

### Properties

#### \_consumer

• `Private` **\_consumer**: _null_ \| [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:7](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L7)

#### \_data

• `Private` **\_data**: Item

Defined in: [yajsapi/executor/smartq.ts:8](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L8)

#### \_prev\_consumers

• `Private` **\_prev\_consumers**: _Set_&lt;[_Consumer_](executor_smartq.consumer.md)&gt;

Defined in: [yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L9)

### Methods

#### assign\_consumer

▸ **assign\_consumer**\(`consumer`: [_Consumer_](executor_smartq.consumer.md)\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `consumer` | [_Consumer_](executor_smartq.consumer.md) |

**Returns:** _void_

Defined in: [yajsapi/executor/smartq.ts:22](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L22)

#### consumer

▸ **consumer**\(\): _null_ \| [_Consumer_](executor_smartq.consumer.md)

**Returns:** _null_ \| [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:18](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L18)

#### data

▸ **data**\(\): Item

**Returns:** Item

Defined in: [yajsapi/executor/smartq.ts:27](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L27)

