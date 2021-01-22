[yajsapi](../README.md) / [Exports](../modules.md) / [executor/smartq](../modules/executor_smartq.md) / Consumer

# Class: Consumer<Item\>

[executor/smartq](../modules/executor_smartq.md).Consumer

## Type parameters

Name |
------ |
`Item` |

## Hierarchy

* **Consumer**

## Table of contents

### Constructors

- [constructor](executor_smartq.consumer.md#constructor)

### Properties

- [\_fetched](executor_smartq.consumer.md#_fetched)
- [\_queue](executor_smartq.consumer.md#_queue)

### Methods

- [[Symbol.asyncIterator]](executor_smartq.consumer.md#[symbol.asynciterator])
- [done](executor_smartq.consumer.md#done)
- [last\_item](executor_smartq.consumer.md#last_item)
- [ready](executor_smartq.consumer.md#ready)

## Constructors

### constructor

\+ **new Consumer**<Item\>(`queue`: [*SmartQueue*](executor_smartq.smartqueue.md)<Item\>): [*Consumer*](executor_smartq.consumer.md)<Item\>

#### Type parameters:

Name |
------ |
`Item` |

#### Parameters:

Name | Type |
------ | ------ |
`queue` | [*SmartQueue*](executor_smartq.smartqueue.md)<Item\> |

**Returns:** [*Consumer*](executor_smartq.consumer.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:153](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L153)

## Properties

### \_fetched

• `Private` `Optional` **\_fetched**: *undefined* \| *null* \| [*Handle*](executor_smartq.handle.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:153](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L153)

___

### \_queue

• `Private` **\_queue**: *any*

Defined in: [yajsapi/executor/smartq.ts:152](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L152)

## Methods

### [Symbol.asyncIterator]

▸ **[Symbol.asyncIterator]**(): *AsyncGenerator*<[*Handle*](executor_smartq.handle.md)<Item\>, *any*, *any*\>

**Returns:** *AsyncGenerator*<[*Handle*](executor_smartq.handle.md)<Item\>, *any*, *any*\>

Defined in: [yajsapi/executor/smartq.ts:173](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L173)

___

### done

▸ **done**(): *null*

**Returns:** *null*

Defined in: [yajsapi/executor/smartq.ts:164](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L164)

___

### last\_item

▸ **last_item**(): *null* \| Item

**Returns:** *null* \| Item

Defined in: [yajsapi/executor/smartq.ts:169](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L169)

___

### ready

▸ **ready**(): [*Consumer*](executor_smartq.consumer.md)<Item\>

**Returns:** [*Consumer*](executor_smartq.consumer.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:160](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L160)
