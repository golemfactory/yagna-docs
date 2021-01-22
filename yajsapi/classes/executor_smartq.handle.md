[yajsapi](../README.md) / [Exports](../modules.md) / [executor/smartq](../modules/executor_smartq.md) / Handle

# Class: Handle<Item\>

[executor/smartq](../modules/executor_smartq.md).Handle

## Type parameters

Name |
------ |
`Item` |

## Hierarchy

* **Handle**

## Table of contents

### Constructors

- [constructor](executor_smartq.handle.md#constructor)

### Properties

- [\_consumer](executor_smartq.handle.md#_consumer)
- [\_data](executor_smartq.handle.md#_data)
- [\_prev\_consumers](executor_smartq.handle.md#_prev_consumers)

### Methods

- [assign\_consumer](executor_smartq.handle.md#assign_consumer)
- [consumer](executor_smartq.handle.md#consumer)
- [data](executor_smartq.handle.md#data)

## Constructors

### constructor

\+ **new Handle**<Item\>(`__namedParameters`: *Object*): [*Handle*](executor_smartq.handle.md)<Item\>

#### Type parameters:

Name |
------ |
`Item` |

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*Handle*](executor_smartq.handle.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L9)

## Properties

### \_consumer

• `Private` **\_consumer**: *null* \| [*Consumer*](executor_smartq.consumer.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:7](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L7)

___

### \_data

• `Private` **\_data**: Item

Defined in: [yajsapi/executor/smartq.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L8)

___

### \_prev\_consumers

• `Private` **\_prev\_consumers**: *Set*<[*Consumer*](executor_smartq.consumer.md)<Item\>\>

Defined in: [yajsapi/executor/smartq.ts:9](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L9)

## Methods

### assign\_consumer

▸ **assign_consumer**(`consumer`: [*Consumer*](executor_smartq.consumer.md)<Item\>): *void*

#### Parameters:

Name | Type |
------ | ------ |
`consumer` | [*Consumer*](executor_smartq.consumer.md)<Item\> |

**Returns:** *void*

Defined in: [yajsapi/executor/smartq.ts:22](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L22)

___

### consumer

▸ **consumer**(): *null* \| [*Consumer*](executor_smartq.consumer.md)<Item\>

**Returns:** *null* \| [*Consumer*](executor_smartq.consumer.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:18](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L18)

___

### data

▸ **data**(): Item

**Returns:** Item

Defined in: [yajsapi/executor/smartq.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L27)
