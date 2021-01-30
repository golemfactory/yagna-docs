# executor/smartq/consumer

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/smartq](../yajsapi-2/executor_smartq.md) / Consumer

## Class: Consumer

[executor/smartq](../yajsapi-2/executor_smartq.md).Consumer

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

+ **new Consumer**\(`queue`: [_SmartQueue_](executor_smartq.smartqueue.md)\): [_Consumer_](executor_smartq.consumer.md)

**Type parameters:**

| Name |
| :--- |
| `Item` |

**Parameters:**

| Name | Type |
| :--- | :--- |
| `queue` | [_SmartQueue_](executor_smartq.smartqueue.md) |

**Returns:** [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:153](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L153)

### Properties

#### \_fetched

• `Private` `Optional` **\_fetched**: _undefined_ \| _null_ \| [_Handle_](executor_smartq.handle.md)

Defined in: [yajsapi/executor/smartq.ts:153](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L153)

#### \_queue

• `Private` **\_queue**: _any_

Defined in: [yajsapi/executor/smartq.ts:152](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L152)

### Methods

#### \[Symbol.asyncIterator\]

▸ **\[Symbol.asyncIterator\]**\(\): _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _any_&gt;

**Returns:** _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _any_&gt;

Defined in: [yajsapi/executor/smartq.ts:173](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L173)

#### done

▸ **done**\(\): _null_

**Returns:** _null_

Defined in: [yajsapi/executor/smartq.ts:164](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L164)

#### last\_item

▸ **last\_item**\(\): _null_ \| Item

**Returns:** _null_ \| Item

Defined in: [yajsapi/executor/smartq.ts:169](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L169)

#### ready

▸ **ready**\(\): [_Consumer_](executor_smartq.consumer.md)

**Returns:** [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:160](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/smartq.ts#L160)

