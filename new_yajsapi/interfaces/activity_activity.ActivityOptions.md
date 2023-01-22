# Interface: ActivityOptions

[activity/activity](../modules/activity_activity.md).ActivityOptions

## Hierarchy

- **`ActivityOptions`**

  ↳ [`TaskOptions`](task_service.TaskOptions.md)

## Table of contents

### Properties

- [yagnaOptions](activity_activity.ActivityOptions.md#yagnaoptions)
- [activityRequestTimeout](activity_activity.ActivityOptions.md#activityrequesttimeout)
- [activityExecuteTimeout](activity_activity.ActivityOptions.md#activityexecutetimeout)
- [activityExeBatchResultsFetchInterval](activity_activity.ActivityOptions.md#activityexebatchresultsfetchinterval)
- [logger](activity_activity.ActivityOptions.md#logger)
- [eventTarget](activity_activity.ActivityOptions.md#eventtarget)
- [taskPackage](activity_activity.ActivityOptions.md#taskpackage)

## Properties

### yagnaOptions

• `Optional` **yagnaOptions**: `Object`

#### Type declaration

| Name | Type | Description |
| :------ | :------ | :------ |
| `apiKey?` | `string` | Yagna Api Key |
| `basePath?` | `string` | Yagna base path to Activity REST Api |

#### Defined in

[yajsapi/activity/activity.ts:30](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L30)

___

### activityRequestTimeout

• `Optional` **activityRequestTimeout**: `number`

timeout for sending and creating batch

#### Defined in

[yajsapi/activity/activity.ts:37](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L37)

___

### activityExecuteTimeout

• `Optional` **activityExecuteTimeout**: `number`

timeout for executing batch

#### Defined in

[yajsapi/activity/activity.ts:39](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L39)

___

### activityExeBatchResultsFetchInterval

• `Optional` **activityExeBatchResultsFetchInterval**: `number`

interval for fetching batch results while polling

#### Defined in

[yajsapi/activity/activity.ts:41](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L41)

___

### logger

• `Optional` **logger**: [`Logger`](utils_logger.Logger.md)

Logger module

#### Defined in

[yajsapi/activity/activity.ts:43](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L43)

___

### eventTarget

• `Optional` **eventTarget**: `EventTarget`

Event Bus implements EventTarget

#### Defined in

[yajsapi/activity/activity.ts:45](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L45)

___

### taskPackage

• `Optional` **taskPackage**: `string`

taskPackage

#### Defined in

[yajsapi/activity/activity.ts:47](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L47)
