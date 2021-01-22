[yajsapi](../README.md) / [Exports](../modules.md) / [executor/task](../modules/executor_task.md) / Task

# Class: Task<TaskData, TaskResult\>

[executor/task](../modules/executor_task.md).Task

One computation unit.

**`description`** Represents one computation unit that will be run on the provider (e.g. rendering of one frame of an animation).

## Type parameters

Name |
------ |
`TaskData` |
`TaskResult` |

## Hierarchy

* **Task**

## Table of contents

### Constructors

- [constructor](executor_task.task.md#constructor)

### Properties

- [\_callbacks](executor_task.task.md#_callbacks)
- [\_data](executor_task.task.md#_data)
- [\_emit\_event](executor_task.task.md#_emit_event)
- [\_finished](executor_task.task.md#_finished)
- [\_handle](executor_task.task.md#_handle)
- [\_result](executor_task.task.md#_result)
- [\_started](executor_task.task.md#_started)
- [\_status](executor_task.task.md#_status)
- [id](executor_task.task.md#id)
- [count](executor_task.task.md#count)

### Accessors

- [counter](executor_task.task.md#counter)

### Methods

- [\_add\_callback](executor_task.task.md#_add_callback)
- [\_start](executor_task.task.md#_start)
- [\_stop](executor_task.task.md#_stop)
- [accept\_result](executor_task.task.md#accept_result)
- [data](executor_task.task.md#data)
- [reject\_result](executor_task.task.md#reject_result)
- [result](executor_task.task.md#result)
- [running\_time](executor_task.task.md#running_time)
- [status](executor_task.task.md#status)
- [for\_handle](executor_task.task.md#for_handle)

## Constructors

### constructor

\+ **new Task**<TaskData, TaskResult\>(`data`: TaskData): [*Task*](executor_task.task.md)<TaskData, TaskResult\>

Create a new Task object.

#### Type parameters:

Name |
------ |
`TaskData` |
`TaskResult` |

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`data` | TaskData | contains information needed to prepare command list for the provider    |

**Returns:** [*Task*](executor_task.task.md)<TaskData, TaskResult\>

Defined in: [yajsapi/executor/task.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L38)

## Properties

### \_callbacks

• `Private` **\_callbacks**: *Set*<*null* \| Function\>

Defined in: [yajsapi/executor/task.ts:31](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L31)

___

### \_data

• `Private` **\_data**: *any*

Defined in: [yajsapi/executor/task.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L37)

___

### \_emit\_event

• `Private` **\_emit\_event**: *any*

Defined in: [yajsapi/executor/task.ts:30](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L30)

___

### \_finished

• `Private` **\_finished**: *null* \| *number*

Defined in: [yajsapi/executor/task.ts:29](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L29)

___

### \_handle

• `Private` `Optional` **\_handle**: *undefined* \| [[*Handle*](executor_smartq.handle.md)<[*Task*](executor_task.task.md)<TaskData, TaskResult\>\>, [*SmartQueue*](executor_smartq.smartqueue.md)<[*Task*](executor_task.task.md)<TaskData, TaskResult\>\>]

Defined in: [yajsapi/executor/task.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L32)

___

### \_result

• `Private` `Optional` **\_result**: *undefined* \| *null* \| TaskResult

Defined in: [yajsapi/executor/task.ts:36](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L36)

___

### \_started

• `Private` **\_started**: *null* \| *number*

Defined in: [yajsapi/executor/task.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L28)

___

### \_status

• `Private` **\_status**: [*TaskStatus*](../enums/executor_task.taskstatus.md)

Defined in: [yajsapi/executor/task.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L38)

___

### id

• **id**: *number*= 0

Defined in: [yajsapi/executor/task.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L27)

___

### count

▪ `Static` **count**: *number*= 0

Defined in: [yajsapi/executor/task.ts:26](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L26)

## Accessors

### counter

• **counter**(): *number*

**Returns:** *number*

Defined in: [yajsapi/executor/task.ts:150](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L150)

## Methods

### \_add\_callback

▸ **_add_callback**(`callback`: Function): *void*

#### Parameters:

Name | Type |
------ | ------ |
`callback` | Function |

**Returns:** *void*

Defined in: [yajsapi/executor/task.ts:59](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L59)

___

### \_start

▸ **_start**(`_emitter`: *any*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`_emitter` | *any* |

**Returns:** *void*

Defined in: [yajsapi/executor/task.ts:63](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L63)

___

### \_stop

▸ **_stop**(`retry?`: *boolean*): *void*

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`retry` | *boolean* | false |

**Returns:** *void*

Defined in: [yajsapi/executor/task.ts:70](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L70)

___

### accept\_result

▸ **accept_result**(`result?`: *null* \| TaskResult): *void*

Accept the result of this task.

**`description`** Must be called when the result is correct to mark this task as completed.

#### Parameters:

Name | Type | Default value | Description |
------ | ------ | ------ | ------ |
`result` | *null* \| TaskResult | null | task computation result (optional)    |

**Returns:** *void*

Defined in: [yajsapi/executor/task.ts:120](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L120)

___

### data

▸ **data**(): TaskData

**Returns:** TaskData

Defined in: [yajsapi/executor/task.ts:95](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L95)

___

### reject\_result

▸ **reject_result**(`reason?`: *null* \| *string*, `retry?`: *boolean*): *void*

Reject the result of this task.

**`description`** Must be called when the result is not correct to indicate that the task should be retried.

#### Parameters:

Name | Type | Default value | Description |
------ | ------ | ------ | ------ |
`reason` | *null* \| *string* | null | Task rejection description (optional)   |
`retry` | *boolean* | false | Task retry in case of rejects (optional)    |

**Returns:** *void*

Defined in: [yajsapi/executor/task.ts:139](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L139)

___

### result

▸ **result**(): *undefined* \| *null* \| TaskResult

**Returns:** *undefined* \| *null* \| TaskResult

Defined in: [yajsapi/executor/task.ts:99](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L99)

___

### running\_time

▸ **running_time**(): *null* \| *number*

**Returns:** *null* \| *number*

Defined in: [yajsapi/executor/task.ts:103](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L103)

___

### status

▸ **status**(): [*TaskStatus*](../enums/executor_task.taskstatus.md)

**Returns:** [*TaskStatus*](../enums/executor_task.taskstatus.md)

Defined in: [yajsapi/executor/task.ts:91](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L91)

___

### for\_handle

▸ `Static`**for_handle**(`handle`: [*Handle*](executor_smartq.handle.md)<[*Task*](executor_task.task.md)<*any*, *any*\>\>, `queue`: [*SmartQueue*](executor_smartq.smartqueue.md)<[*Task*](executor_task.task.md)<*any*, *any*\>\>, `emitter`: [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](executor_events.yaevent.md)], *void*\>): [*Task*](executor_task.task.md)<*TaskData*, *TaskResult*\>

#### Parameters:

Name | Type |
------ | ------ |
`handle` | [*Handle*](executor_smartq.handle.md)<[*Task*](executor_task.task.md)<*any*, *any*\>\> |
`queue` | [*SmartQueue*](executor_smartq.smartqueue.md)<[*Task*](executor_task.task.md)<*any*, *any*\>\> |
`emitter` | [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](executor_events.yaevent.md)], *void*\> |

**Returns:** [*Task*](executor_task.task.md)<*TaskData*, *TaskResult*\>

Defined in: [yajsapi/executor/task.ts:80](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L80)
