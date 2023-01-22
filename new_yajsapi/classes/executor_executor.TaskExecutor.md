# Class: TaskExecutor

[executor/executor](../modules/executor_executor.md).TaskExecutor

## Table of contents

### Methods

- [create](executor_executor.TaskExecutor.md#create)
- [init](executor_executor.TaskExecutor.md#init)
- [end](executor_executor.TaskExecutor.md#end)
- [getStats](executor_executor.TaskExecutor.md#getstats)
- [beforeEach](executor_executor.TaskExecutor.md#beforeeach)
- [run](executor_executor.TaskExecutor.md#run)
- [map](executor_executor.TaskExecutor.md#map)
- [forEach](executor_executor.TaskExecutor.md#foreach)

## High-level

### create

▸ `Static` **create**(`options`): `Promise`<[`TaskExecutor`](executor_executor.TaskExecutor.md)\>

Create a new Task Executor

**`Description`**

Factory Method that create and initialize an instance of the TaskExecutor

**`Example`**

**Simple usage of Task Executor**

The executor can be created by passing appropriate initial parameters such as package, budget, subnet tag, payment driver, payment network etc.
One required parameter is a package. This can be done in two ways. First by passing only package image hash, e.g.
```js
const executor = await TaskExecutor.create("9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae");
```

**`Example`**

**Usage of Task Executor with custom parameters**

Or by passing some optional parameters, e.g.
```js
const executor = await TaskExecutor.create({
  subnetTag: "public",
  payment: { driver: "erc-20", network: "rinkeby" },
  package: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
});
```

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `options` | [`ExecutorOptionsMixin`](../modules/executor_executor.md#executoroptionsmixin) | Task executor options |

#### Returns

`Promise`<[`TaskExecutor`](executor_executor.TaskExecutor.md)\>

TaskExecutor

#### Defined in

[yajsapi/executor/executor.ts:103](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L103)

## Other

### init

▸ **init**(): `Promise`<`void`\>

Initialize executor

**`Description`**

Method responsible initialize all executor services.

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/executor/executor.ts:142](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L142)

___

### end

▸ **end**(): `Promise`<`void`\>

End executor process

**`Description`**

Method responsible for stopping all executor services and shut down executor instance

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/executor/executor.ts:167](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L167)

___

### getStats

▸ **getStats**(): `Object`

Statistics of execution process

#### Returns

`Object`

array

#### Defined in

[yajsapi/executor/executor.ts:187](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L187)

___

### beforeEach

▸ **beforeEach**(`worker`): `void`

Define worker function that will be runs before every each computation Task

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `worker` | [`Worker`](../modules/task_work.md#worker)<`unknown`, `unknown`\> | worker function |

#### Returns

`void`

#### Defined in

[yajsapi/executor/executor.ts:196](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L196)

___

### run

▸ **run**<`OutputType`\>(`worker`): `Promise`<`undefined` \| `OutputType`\>

Run task

#### Type parameters

| Name | Type |
| :------ | :------ |
| `OutputType` | [`Result`](../interfaces/activity_results.Result.md) |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `worker` | [`Worker`](../modules/task_work.md#worker)<`undefined`, `OutputType`\> | function that run task |

#### Returns

`Promise`<`undefined` \| `OutputType`\>

computed task

#### Defined in

[yajsapi/executor/executor.ts:206](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L206)

___

### map

▸ **map**<`InputType`, `OutputType`\>(`data`, `worker`): `AsyncIterable`<`undefined` \| `OutputType`\>

Map iterable data to worker function and return computed Task result as AsyncIterable

#### Type parameters

| Name |
| :------ |
| `InputType` |
| `OutputType` |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Iterable`<`InputType`\> | Iterable data |
| `worker` | [`Worker`](../modules/task_work.md#worker)<`InputType`, `OutputType`\> | worker function |

#### Returns

`AsyncIterable`<`undefined` \| `OutputType`\>

AsyncIterable with results of computed tasks

#### Defined in

[yajsapi/executor/executor.ts:217](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L217)

___

### forEach

▸ **forEach**<`InputType`, `OutputType`\>(`data`, `worker`): `Promise`<`void`\>

Iterates over given data and execute task using worker function

#### Type parameters

| Name |
| :------ |
| `InputType` |
| `OutputType` |

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `data` | `Iterable`<`InputType`\> | Iterable data |
| `worker` | [`Worker`](../modules/task_work.md#worker)<`InputType`, `OutputType`\> | Worker function |

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/executor/executor.ts:256](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L256)
