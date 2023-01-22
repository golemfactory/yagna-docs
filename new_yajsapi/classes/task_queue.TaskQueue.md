# Class: TaskQueue<Task\>

[task/queue](../modules/task_queue.md).TaskQueue

## Type parameters

| Name | Type |
| :------ | :------ |
| `Task` | extends [`QueueableTask`](../interfaces/task_queue.QueueableTask.md) |

## Table of contents

### Constructors

- [constructor](task_queue.TaskQueue.md#constructor)

### Properties

- [itemsStack](task_queue.TaskQueue.md#itemsstack)

### Methods

- [addToEnd](task_queue.TaskQueue.md#addtoend)
- [addToBegin](task_queue.TaskQueue.md#addtobegin)
- [get](task_queue.TaskQueue.md#get)

### Accessors

- [size](task_queue.TaskQueue.md#size)

## Constructors

### constructor

• **new TaskQueue**<`Task`\>()

#### Type parameters

| Name | Type |
| :------ | :------ |
| `Task` | extends [`QueueableTask`](../interfaces/task_queue.QueueableTask.md) |

## Properties

### itemsStack

• `Protected` **itemsStack**: `Task`[] = `[]`

#### Defined in

[yajsapi/task/queue.ts:6](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/queue.ts#L6)

## Methods

### addToEnd

▸ **addToEnd**(`task`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `task` | `Task` |

#### Returns

`void`

#### Defined in

[yajsapi/task/queue.ts:8](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/queue.ts#L8)

___

### addToBegin

▸ **addToBegin**(`task`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `task` | `Task` |

#### Returns

`void`

#### Defined in

[yajsapi/task/queue.ts:13](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/queue.ts#L13)

___

### get

▸ **get**(): `undefined` \| `Task`

#### Returns

`undefined` \| `Task`

#### Defined in

[yajsapi/task/queue.ts:22](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/queue.ts#L22)

## Accessors

### size

• `get` **size**(): `number`

#### Returns

`number`

#### Defined in

[yajsapi/task/queue.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/queue.ts#L18)
