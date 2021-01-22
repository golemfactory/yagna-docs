[yajsapi](../README.md) / [Exports](../modules.md) / [utils/queue](../modules/utils_queue.md) / default

# Class: default<T\>

[utils/queue](../modules/utils_queue.md).default

## Type parameters

Name |
------ |
`T` |

## Hierarchy

* **default**

## Table of contents

### Constructors

- [constructor](utils_queue.default.md#constructor)

### Properties

- [\_cancellationToken](utils_queue.default.md#_cancellationtoken)
- [\_tasks](utils_queue.default.md#_tasks)

### Methods

- [empty](utils_queue.default.md#empty)
- [get](utils_queue.default.md#get)
- [put](utils_queue.default.md#put)

## Constructors

### constructor

\+ **new default**<T\>(`list?`: *never*[], `cancellationToken`: *any*): [*default*](utils_queue.default.md)<T\>

#### Type parameters:

Name |
------ |
`T` |

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`list` | *never*[] | ... |
`cancellationToken` | *any* | - |

**Returns:** [*default*](utils_queue.default.md)<T\>

Defined in: [yajsapi/utils/queue.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L5)

## Properties

### \_cancellationToken

• `Private` **\_cancellationToken**: *any*

Defined in: [yajsapi/utils/queue.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L5)

___

### \_tasks

• `Private` **\_tasks**: *any*

Defined in: [yajsapi/utils/queue.ts:4](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L4)

## Methods

### empty

▸ **empty**(): *boolean*

**Returns:** *boolean*

Defined in: [yajsapi/utils/queue.ts:33](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L33)

___

### get

▸ **get**(): *Promise*<T\>

**Returns:** *Promise*<T\>

Defined in: [yajsapi/utils/queue.ts:20](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L20)

___

### put

▸ **put**(`item`: T): *void*

#### Parameters:

Name | Type |
------ | ------ |
`item` | T |

**Returns:** *void*

Defined in: [yajsapi/utils/queue.ts:16](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/queue.ts#L16)
