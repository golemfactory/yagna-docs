# Class: Consumer

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/smartq](../modules/executor_smartq.md) / Consumer

## Class: Consumer

[executor/smartq](../modules/executor_smartq.md).Consumer

### Type parameters

| Name |
| :--- |
| `Item` |

### Hierarchy

* **Consumer**

### Table of contents

#### Constructors

* [constructor](executor_smartq.consumer.md#constructor)

#### Properties

* [\_fetched](executor_smartq.consumer.md#_fetched)
* [\_queue](executor_smartq.consumer.md#_queue)

#### Methods

* [\[Symbol.asyncIterator\]](executor_smartq.consumer.md#[symbol.asynciterator])
* [done](executor_smartq.consumer.md#done)
* [last\_item](executor_smartq.consumer.md#last_item)
* [ready](executor_smartq.consumer.md#ready)

### Constructors

#### constructor

* **new Consumer**\(`queue`: [_SmartQueue_](executor_smartq.smartqueue.md)\): [_Consumer_](executor_smartq.consumer.md)

**Type parameters:**

| Name |
| :--- |
| `Item` |

**Parameters:**

| Name | Type |
| :--- | :--- |
| `queue` | [_SmartQueue_](executor_smartq.smartqueue.md) |

**Returns:** [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:167](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L167)

### Properties

#### \_fetched

• `Private` `Optional` **\_fetched**: _undefined_ \| _null_ \| [_Handle_](executor_smartq.handle.md)

Defined in: [yajsapi/executor/smartq.ts:167](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L167)

#### \_queue

• `Private` **\_queue**: _any_

Defined in: [yajsapi/executor/smartq.ts:166](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L166)

### Methods

#### \[Symbol.asyncIterator\]

▸ **\[Symbol.asyncIterator\]**\(\): _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _any_&gt;

**Returns:** _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _any_&gt;

Defined in: [yajsapi/executor/smartq.ts:187](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L187)

#### done

▸ **done**\(\): _null_

**Returns:** _null_

Defined in: [yajsapi/executor/smartq.ts:178](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L178)

#### last\_item

▸ **last\_item**\(\): _null_ \| Item

**Returns:** _null_ \| Item

Defined in: [yajsapi/executor/smartq.ts:183](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L183)

#### ready

▸ **ready**\(\): [_Consumer_](executor_smartq.consumer.md)

**Returns:** [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:174](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L174)

