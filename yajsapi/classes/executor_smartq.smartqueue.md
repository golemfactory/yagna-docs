# Class: SmartQueue

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/smartq](../modules/executor_smartq.md) / SmartQueue

## Class: SmartQueue

[executor/smartq](../modules/executor_smartq.md).SmartQueue

### Type parameters

| Name |
| :--- |
| `Item` |

### Hierarchy

* **SmartQueue**

### Table of contents

#### Constructors

* [constructor](executor_smartq.smartqueue.md#constructor)

#### Properties

* [\_\_done](executor_smartq.smartqueue.md#__done)
* [\_\_eof](executor_smartq.smartqueue.md#__eof)
* [\_\_new\_items](executor_smartq.smartqueue.md#__new_items)
* [\_in\_progress](executor_smartq.smartqueue.md#_in_progress)
* [\_items](executor_smartq.smartqueue.md#_items)
* [\_rescheduled\_items](executor_smartq.smartqueue.md#_rescheduled_items)

#### Methods

* [\_\_find\_rescheduled\_item](executor_smartq.smartqueue.md#__find_rescheduled_item)
* [\_\_have\_data](executor_smartq.smartqueue.md#__have_data)
* [close](executor_smartq.smartqueue.md#close)
* [get](executor_smartq.smartqueue.md#get)
* [has\_unassigned\_items](executor_smartq.smartqueue.md#has_unassigned_items)
* [mark\_done](executor_smartq.smartqueue.md#mark_done)
* [new\_consumer](executor_smartq.smartqueue.md#new_consumer)
* [reschedule](executor_smartq.smartqueue.md#reschedule)
* [reschedule\_all](executor_smartq.smartqueue.md#reschedule_all)
* [stats](executor_smartq.smartqueue.md#stats)
* [wait\_until\_done](executor_smartq.smartqueue.md#wait_until_done)

### Constructors

#### constructor

* **new SmartQueue**\(`items`: Item\[\], `retry_cnt?`: _number_, ...`rest`: _any_\[\]\): [_SmartQueue_](executor_smartq.smartqueue.md)

**Type parameters:**

| Name |
| :--- |
| `Item` |

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `items` | Item\[\] | - |
| `retry_cnt` | _number_ | 2 |
| `...rest` | _any_\[\] | - |

**Returns:** [_SmartQueue_](executor_smartq.smartqueue.md)

Defined in: [yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L38)

### Properties

#### \_\_done

• `Private` **\_\_done**: _any_

Defined in: [yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L38)

#### \_\_eof

• `Private` **\_\_eof**: _any_

Defined in: [yajsapi/executor/smartq.ts:37](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L37)

#### \_\_new\_items

• `Private` **\_\_new\_items**: _any_

Defined in: [yajsapi/executor/smartq.ts:36](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L36)

#### \_in\_progress

• `Private` **\_in\_progress**: _Set_&lt;[_Handle_](executor_smartq.handle.md)&gt;

Defined in: [yajsapi/executor/smartq.ts:35](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L35)

#### \_items

• `Private` **\_items**: _null_ \| Item\[\]

Defined in: [yajsapi/executor/smartq.ts:33](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L33)

#### \_rescheduled\_items

• `Private` **\_rescheduled\_items**: _Set_&lt;[_Handle_](executor_smartq.handle.md)&gt;

Defined in: [yajsapi/executor/smartq.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L34)

### Methods

#### \_\_find\_rescheduled\_item

▸ **\_\_find\_rescheduled\_item**\(`consumer`: [_Consumer_](executor_smartq.consumer.md)\): _null_ \| [_Handle_](executor_smartq.handle.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `consumer` | [_Consumer_](executor_smartq.consumer.md) |

**Returns:** _null_ \| [_Handle_](executor_smartq.handle.md)

Defined in: [yajsapi/executor/smartq.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L71)

#### \_\_have\_data

▸ **\_\_have\_data**\(\): _boolean_

**Returns:** _boolean_

Defined in: [yajsapi/executor/smartq.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L63)

#### close

▸ **close**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/executor/smartq.ts:50](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L50)

#### get

▸ **get**\(`consumer`: [_Consumer_](executor_smartq.consumer.md), `callback`: _undefined_ \| _null_ \| Function\): _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _unknown_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `consumer` | [_Consumer_](executor_smartq.consumer.md) |
| `callback` | _undefined_ \| _null_ \| Function |

**Returns:** _AsyncGenerator_&lt;[_Handle_](executor_smartq.handle.md), _any_, _unknown_&gt;

Defined in: [yajsapi/executor/smartq.ts:78](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L78)

#### has\_unassigned\_items

▸ **has\_unassigned\_items**\(\): _boolean_

**Returns:** _boolean_

Defined in: [yajsapi/executor/smartq.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L160)

#### mark\_done

▸ **mark\_done**\(`handle`: [_Handle_](executor_smartq.handle.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `handle` | [_Handle_](executor_smartq.handle.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/smartq.ts:112](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L112)

#### new\_consumer

▸ **new\_consumer**\(\): [_Consumer_](executor_smartq.consumer.md)

**Returns:** [_Consumer_](executor_smartq.consumer.md)

Defined in: [yajsapi/executor/smartq.ts:59](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L59)

#### reschedule

▸ **reschedule**\(`handle`: [_Handle_](executor_smartq.handle.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `handle` | [_Handle_](executor_smartq.handle.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/smartq.ts:124](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L124)

#### reschedule\_all

▸ **reschedule\_all**\(`consumer`: [_Consumer_](executor_smartq.consumer.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `consumer` | [_Consumer_](executor_smartq.consumer.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/smartq.ts:132](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L132)

#### stats

▸ **stats**\(\): _object_

**Returns:** _object_

Defined in: [yajsapi/executor/smartq.ts:146](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L146)

#### wait\_until\_done

▸ **wait\_until\_done**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/smartq.ts:154](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L154)

