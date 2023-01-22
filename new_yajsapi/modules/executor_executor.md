# Module: executor/executor

## Table of contents

### Type Aliases

- [ExecutorOptions](executor_executor.md#executoroptions)
- [ExecutorOptionsMixin](executor_executor.md#executoroptionsmixin)
- [YagnaOptions](executor_executor.md#yagnaoptions)

### Classes

- [TaskExecutor](../classes/executor_executor.TaskExecutor.md)

## High-level

### ExecutorOptions

Ƭ **ExecutorOptions**: { `package`: `string` \| [`Package`](../classes/package_package.Package.md) ; `taskTimeout?`: `number` ; `subnetTag?`: `string` ; `logger?`: [`Logger`](../interfaces/utils_logger.Logger.md) ; `logLevel?`: [`LogLevel`](../enums/utils_logger.LogLevel.md) \| `string` ; `yagnaOptions?`: [`YagnaOptions`](executor_executor.md#yagnaoptions) ; `eventTarget?`: `EventTarget`  } & [`ActivityOptions`](../interfaces/activity_activity.ActivityOptions.md) & [`AgreementOptions`](../interfaces/agreement_agreement.AgreementOptions.md) & [`BasePaymentOptions`](../interfaces/payment_config.BasePaymentOptions.md) & [`DemandOptions`](../interfaces/market_demand.DemandOptions.md) & `Omit`<[`PackageOptions`](../interfaces/package_package.PackageOptions.md), ``"imageHash"``\> & [`TaskOptions`](../interfaces/task_service.TaskOptions.md) & [`NetworkServiceOptions`](network_service.md#networkserviceoptions) & [`AgreementServiceOptions`](../interfaces/agreement_service.AgreementServiceOptions.md) & `Omit`<[`WorkOptions`](../interfaces/task_work.WorkOptions.md), ``"isRunning"``\>

#### Defined in

[yajsapi/executor/executor.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L23)

___

## Other

### ExecutorOptionsMixin

Ƭ **ExecutorOptionsMixin**: `string` \| [`ExecutorOptions`](executor_executor.md#executoroptions)

Contains information needed to start executor, if string the imageHash is required, otherwise it should be a type of [ExecutorOptions](executor_executor.md#executoroptions)

#### Defined in

[yajsapi/executor/executor.ts:51](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L51)

___

### YagnaOptions

Ƭ **YagnaOptions**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `apiKey` | `string` |
| `basePath` | `string` |

#### Defined in

[yajsapi/executor/executor.ts:53](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/executor.ts#L53)
