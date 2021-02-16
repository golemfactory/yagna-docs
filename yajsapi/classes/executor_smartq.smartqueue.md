[yajsapi](../README.md) / [Exports](../modules.md) / [executor/smartq](../modules/executor_smartq.md) / SmartQueue

# Class: SmartQueue<Item\>

[executor/smartq](../modules/executor_smartq.md).SmartQueue

## Type parameters

Name |
------ |
`Item` |

## Hierarchy

* **SmartQueue**

## Table of contents

### Constructors

- [constructor](executor_smartq.smartqueue.md#constructor)

### Properties

- [\_\_done](executor_smartq.smartqueue.md#__done)
- [\_\_eof](executor_smartq.smartqueue.md#__eof)
- [\_\_new\_items](executor_smartq.smartqueue.md#__new_items)
- [\_in\_progress](executor_smartq.smartqueue.md#_in_progress)
- [\_items](executor_smartq.smartqueue.md#_items)
- [\_rescheduled\_items](executor_smartq.smartqueue.md#_rescheduled_items)

### Methods

- [\_\_find\_rescheduled\_item](executor_smartq.smartqueue.md#__find_rescheduled_item)
- [\_\_have\_data](executor_smartq.smartqueue.md#__have_data)
- [close](executor_smartq.smartqueue.md#close)
- [get](executor_smartq.smartqueue.md#get)
- [has\_unassigned\_items](executor_smartq.smartqueue.md#has_unassigned_items)
- [mark\_done](executor_smartq.smartqueue.md#mark_done)
- [new\_consumer](executor_smartq.smartqueue.md#new_consumer)
- [reschedule](executor_smartq.smartqueue.md#reschedule)
- [reschedule\_all](executor_smartq.smartqueue.md#reschedule_all)
- [stats](executor_smartq.smartqueue.md#stats)
- [wait\_until\_done](executor_smartq.smartqueue.md#wait_until_done)

## Constructors

### constructor

\+ **new SmartQueue**<Item\>(`items`: Item[], `retry_cnt?`: *number*, ...`rest`: *any*[]): [*SmartQueue*](executor_smartq.smartqueue.md)<Item\>

#### Type parameters:

Name |
------ |
`Item` |

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`items` | Item[] | - |
`retry_cnt` | *number* | 2 |
`...rest` | *any*[] | - |

**Returns:** [*SmartQueue*](executor_smartq.smartqueue.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L38)

## Properties

### \_\_done

• `Private` **\_\_done**: *any*

Defined in: [yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L38)

___

### \_\_eof

• `Private` **\_\_eof**: *any*

Defined in: [yajsapi/executor/smartq.ts:37](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L37)

___

### \_\_new\_items

• `Private` **\_\_new\_items**: *any*

Defined in: [yajsapi/executor/smartq.ts:36](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L36)

___

### \_in\_progress

• `Private` **\_in\_progress**: *Set*<[*Handle*](executor_smartq.handle.md)<Item\>\>

Defined in: [yajsapi/executor/smartq.ts:35](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L35)

___

### \_items

• `Private` **\_items**: *null* \| Item[]

Defined in: [yajsapi/executor/smartq.ts:33](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L33)

___

### \_rescheduled\_items

• `Private` **\_rescheduled\_items**: *Set*<[*Handle*](executor_smartq.handle.md)<Item\>\>

Defined in: [yajsapi/executor/smartq.ts:34](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L34)

## Methods

### \_\_find\_rescheduled\_item

▸ **__find_rescheduled_item**(`consumer`: [*Consumer*](executor_smartq.consumer.md)<Item\>): *null* \| [*Handle*](executor_smartq.handle.md)<Item\>

#### Parameters:

Name | Type |
------ | ------ |
`consumer` | [*Consumer*](executor_smartq.consumer.md)<Item\> |

**Returns:** *null* \| [*Handle*](executor_smartq.handle.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L71)

___

### \_\_have\_data

▸ **__have_data**(): *boolean*

**Returns:** *boolean*

Defined in: [yajsapi/executor/smartq.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L63)

___

### close

▸ **close**(): *void*

**Returns:** *void*

Defined in: [yajsapi/executor/smartq.ts:50](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L50)

___

### get

▸ **get**(`consumer`: [*Consumer*](executor_smartq.consumer.md)<Item\>, `callback`: *undefined* \| *null* \| Function): *AsyncGenerator*<[*Handle*](executor_smartq.handle.md)<Item\>, *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`consumer` | [*Consumer*](executor_smartq.consumer.md)<Item\> |
`callback` | *undefined* \| *null* \| Function |

**Returns:** *AsyncGenerator*<[*Handle*](executor_smartq.handle.md)<Item\>, *any*, *unknown*\>

Defined in: [yajsapi/executor/smartq.ts:78](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L78)

___

### has\_unassigned\_items

▸ **has_unassigned_items**(): *boolean*

**Returns:** *boolean*

Defined in: [yajsapi/executor/smartq.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L160)

___

### mark\_done

▸ **mark_done**(`handle`: [*Handle*](executor_smartq.handle.md)<Item\>): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`handle` | [*Handle*](executor_smartq.handle.md)<Item\> |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/smartq.ts:112](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L112)

___

### new\_consumer

▸ **new_consumer**(): [*Consumer*](executor_smartq.consumer.md)<Item\>

**Returns:** [*Consumer*](executor_smartq.consumer.md)<Item\>

Defined in: [yajsapi/executor/smartq.ts:59](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L59)

___

### reschedule

▸ **reschedule**(`handle`: [*Handle*](executor_smartq.handle.md)<Item\>): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`handle` | [*Handle*](executor_smartq.handle.md)<Item\> |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/smartq.ts:124](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L124)

___

### reschedule\_all

▸ **reschedule_all**(`consumer`: [*Consumer*](executor_smartq.consumer.md)<Item\>): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`consumer` | [*Consumer*](executor_smartq.consumer.md)<Item\> |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/smartq.ts:132](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L132)

___

### stats

▸ **stats**(): *object*

**Returns:** *object*

Defined in: [yajsapi/executor/smartq.ts:146](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L146)

___

### wait\_until\_done

▸ **wait_until_done**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/smartq.ts:154](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/smartq.ts#L154)
