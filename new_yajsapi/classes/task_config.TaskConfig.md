# Class: TaskConfig

[task/config](../modules/task_config.md).TaskConfig

## Hierarchy

- `ActivityConfig`

  ↳ **`TaskConfig`**

## Table of contents

### Constructors

- [constructor](task_config.TaskConfig.md#constructor)

### Properties

- [maxParallelTasks](task_config.TaskConfig.md#maxparalleltasks)
- [taskRunningInterval](task_config.TaskConfig.md#taskrunninginterval)
- [taskTimeout](task_config.TaskConfig.md#tasktimeout)
- [activityStateCheckingInterval](task_config.TaskConfig.md#activitystatecheckinginterval)
- [storageProvider](task_config.TaskConfig.md#storageprovider)
- [logger](task_config.TaskConfig.md#logger)
- [api](task_config.TaskConfig.md#api)
- [activityRequestTimeout](task_config.TaskConfig.md#activityrequesttimeout)
- [activityExecuteTimeout](task_config.TaskConfig.md#activityexecutetimeout)
- [activityExeBatchResultsFetchInterval](task_config.TaskConfig.md#activityexebatchresultsfetchinterval)
- [eventTarget](task_config.TaskConfig.md#eventtarget)
- [yagnaOptions](task_config.TaskConfig.md#yagnaoptions)

## Constructors

### constructor

• **new TaskConfig**(`options?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `options?` | [`TaskOptions`](../interfaces/task_service.TaskOptions.md) |

#### Overrides

ActivityConfig.constructor

#### Defined in

[yajsapi/task/config.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L21)

## Properties

### maxParallelTasks

• `Readonly` **maxParallelTasks**: `number`

#### Defined in

[yajsapi/task/config.ts:14](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L14)

___

### taskRunningInterval

• `Readonly` **taskRunningInterval**: `number`

#### Defined in

[yajsapi/task/config.ts:15](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L15)

___

### taskTimeout

• `Readonly` **taskTimeout**: `number`

#### Defined in

[yajsapi/task/config.ts:16](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L16)

___

### activityStateCheckingInterval

• `Readonly` **activityStateCheckingInterval**: `number`

#### Defined in

[yajsapi/task/config.ts:17](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L17)

___

### storageProvider

• `Optional` `Readonly` **storageProvider**: [`StorageProvider`](../interfaces/storage_provider.StorageProvider.md)

#### Defined in

[yajsapi/task/config.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L18)

___

### logger

• `Optional` `Readonly` **logger**: [`Logger`](../interfaces/utils_logger.Logger.md)

#### Overrides

ActivityConfig.logger

#### Defined in

[yajsapi/task/config.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/task/config.ts#L19)

___

### api

• `Readonly` **api**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `control` | `RequestorControlApi` |
| `state` | `RequestorStateApi` |

#### Inherited from

ActivityConfig.api

#### Defined in

[yajsapi/activity/config.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L18)

___

### activityRequestTimeout

• `Readonly` **activityRequestTimeout**: `number`

#### Inherited from

ActivityConfig.activityRequestTimeout

#### Defined in

[yajsapi/activity/config.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L19)

___

### activityExecuteTimeout

• `Readonly` **activityExecuteTimeout**: `number`

#### Inherited from

ActivityConfig.activityExecuteTimeout

#### Defined in

[yajsapi/activity/config.ts:20](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L20)

___

### activityExeBatchResultsFetchInterval

• `Readonly` **activityExeBatchResultsFetchInterval**: `number`

#### Inherited from

ActivityConfig.activityExeBatchResultsFetchInterval

#### Defined in

[yajsapi/activity/config.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L21)

___

### eventTarget

• `Optional` `Readonly` **eventTarget**: `EventTarget`

#### Inherited from

ActivityConfig.eventTarget

#### Defined in

[yajsapi/activity/config.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L23)

___

### yagnaOptions

• `Readonly` **yagnaOptions**: [`YagnaOptions`](../modules/executor_executor.md#yagnaoptions)

#### Inherited from

ActivityConfig.yagnaOptions

#### Defined in

[yajsapi/activity/config.ts:24](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/config.ts#L24)
