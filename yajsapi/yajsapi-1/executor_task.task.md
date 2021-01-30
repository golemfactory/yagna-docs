# executor/task/task

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/task](../yajsapi-2/executor_task.md) / Task

## Class: Task

[executor/task](../yajsapi-2/executor_task.md).Task

One computation unit.

**`description`** Represents one computation unit that will be run on the provider \(e.g. rendering of one frame of an animation\).

### Type parameters

| Name |
| :--- |
| `TaskData` |
| `TaskResult` |

### Hierarchy

* **Task**

### Table of contents

#### Constructors

* [constructor](executor_task.task.md#constructor)

#### Properties

* [\_callbacks](executor_task.task.md#_callbacks)
* [\_data](executor_task.task.md#_data)
* [\_emit\_event](executor_task.task.md#_emit_event)
* [\_finished](executor_task.task.md#_finished)
* [\_handle](executor_task.task.md#_handle)
* [\_result](executor_task.task.md#_result)
* [\_started](executor_task.task.md#_started)
* [\_status](executor_task.task.md#_status)
* [id](executor_task.task.md#id)
* [count](executor_task.task.md#count)

#### Accessors

* [counter](executor_task.task.md#counter)

#### Methods

* [\_add\_callback](executor_task.task.md#_add_callback)
* [\_start](executor_task.task.md#_start)
* [\_stop](executor_task.task.md#_stop)
* [accept\_result](executor_task.task.md#accept_result)
* [data](executor_task.task.md#data)
* [reject\_result](executor_task.task.md#reject_result)
* [result](executor_task.task.md#result)
* [running\_time](executor_task.task.md#running_time)
* [status](executor_task.task.md#status)
* [for\_handle](executor_task.task.md#for_handle)

### Constructors

#### constructor

+ **new Task**\(`data`: TaskData\): [_Task_](executor_task.task.md)

Create a new Task object.

**Type parameters:**

| Name |
| :--- |
| `TaskData` |
| `TaskResult` |

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `data` | TaskData | contains information needed to prepare command list for the provider |

**Returns:** [_Task_](executor_task.task.md)

Defined in: [yajsapi/executor/task.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L38)

### Properties

#### \_callbacks

• `Private` **\_callbacks**: _Set_&lt;_null_ \| Function&gt;

Defined in: [yajsapi/executor/task.ts:31](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L31)

#### \_data

• `Private` **\_data**: _any_

Defined in: [yajsapi/executor/task.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L37)

#### \_emit\_event

• `Private` **\_emit\_event**: _any_

Defined in: [yajsapi/executor/task.ts:30](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L30)

#### \_finished

• `Private` **\_finished**: _null_ \| _number_

Defined in: [yajsapi/executor/task.ts:29](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L29)

#### \_handle

• `Private` `Optional` **\_handle**: _undefined_ \| \[[_Handle_](executor_smartq.handle.md)&lt;[_Task_](executor_task.task.md)&gt;, [_SmartQueue_](executor_smartq.smartqueue.md)&lt;[_Task_](executor_task.task.md)&gt;\]

Defined in: [yajsapi/executor/task.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L32)

#### \_result

• `Private` `Optional` **\_result**: _undefined_ \| _null_ \| TaskResult

Defined in: [yajsapi/executor/task.ts:36](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L36)

#### \_started

• `Private` **\_started**: _null_ \| _number_

Defined in: [yajsapi/executor/task.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L28)

#### \_status

• `Private` **\_status**: [_TaskStatus_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/enums/executor_task.taskstatus.md)

Defined in: [yajsapi/executor/task.ts:38](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L38)

#### id

• **id**: _number_= 0

Defined in: [yajsapi/executor/task.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L27)

#### count

▪ `Static` **count**: _number_= 0

Defined in: [yajsapi/executor/task.ts:26](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L26)

### Accessors

#### counter

• **counter**\(\): _number_

**Returns:** _number_

Defined in: [yajsapi/executor/task.ts:150](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L150)

### Methods

#### \_add\_callback

▸ **\_add\_callback**\(`callback`: Function\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `callback` | Function |

**Returns:** _void_

Defined in: [yajsapi/executor/task.ts:59](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L59)

#### \_start

▸ **\_start**\(`_emitter`: _any_\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `_emitter` | _any_ |

**Returns:** _void_

Defined in: [yajsapi/executor/task.ts:63](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L63)

#### \_stop

▸ **\_stop**\(`retry?`: _boolean_\): _void_

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `retry` | _boolean_ | false |

**Returns:** _void_

Defined in: [yajsapi/executor/task.ts:70](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L70)

#### accept\_result

▸ **accept\_result**\(`result?`: _null_ \| TaskResult\): _void_

Accept the result of this task.

**`description`** Must be called when the result is correct to mark this task as completed.

**Parameters:**

| Name | Type | Default value | Description |
| :--- | :--- | :--- | :--- |
| `result` | _null_ \| TaskResult | null | task computation result \(optional\) |

**Returns:** _void_

Defined in: [yajsapi/executor/task.ts:120](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L120)

#### data

▸ **data**\(\): TaskData

**Returns:** TaskData

Defined in: [yajsapi/executor/task.ts:95](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L95)

#### reject\_result

▸ **reject\_result**\(`reason?`: _null_ \| _string_, `retry?`: _boolean_\): _void_

Reject the result of this task.

**`description`** Must be called when the result is not correct to indicate that the task should be retried.

**Parameters:**

| Name | Type | Default value | Description |
| :--- | :--- | :--- | :--- |
| `reason` | _null_ \| _string_ | null | Task rejection description \(optional\) |
| `retry` | _boolean_ | false | Task retry in case of rejects \(optional\) |

**Returns:** _void_

Defined in: [yajsapi/executor/task.ts:139](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L139)

#### result

▸ **result**\(\): _undefined_ \| _null_ \| TaskResult

**Returns:** _undefined_ \| _null_ \| TaskResult

Defined in: [yajsapi/executor/task.ts:99](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L99)

#### running\_time

▸ **running\_time**\(\): _null_ \| _number_

**Returns:** _null_ \| _number_

Defined in: [yajsapi/executor/task.ts:103](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L103)

#### status

▸ **status**\(\): [_TaskStatus_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/enums/executor_task.taskstatus.md)

**Returns:** [_TaskStatus_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/enums/executor_task.taskstatus.md)

Defined in: [yajsapi/executor/task.ts:91](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L91)

#### for\_handle

▸ `Static`**for\_handle**\(`handle`: [_Handle_](executor_smartq.handle.md)&lt;[_Task_](executor_task.task.md)&lt;_any_, _any_&gt;&gt;, `queue`: [_SmartQueue_](executor_smartq.smartqueue.md)&lt;[_Task_](executor_task.task.md)&lt;_any_, _any_&gt;&gt;, `emitter`: [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_YaEvent_](executor_events.yaevent.md)\], _void_&gt;\): [_Task_](executor_task.task.md)&lt;_TaskData_, _TaskResult_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `handle` | [_Handle_](executor_smartq.handle.md)&lt;[_Task_](executor_task.task.md)&lt;_any_, _any_&gt;&gt; |
| `queue` | [_SmartQueue_](executor_smartq.smartqueue.md)&lt;[_Task_](executor_task.task.md)&lt;_any_, _any_&gt;&gt; |
| `emitter` | [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_YaEvent_](executor_events.yaevent.md)\], _void_&gt; |

**Returns:** [_Task_](executor_task.task.md)&lt;_TaskData_, _TaskResult_&gt;

Defined in: [yajsapi/executor/task.ts:80](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/task.ts#L80)

