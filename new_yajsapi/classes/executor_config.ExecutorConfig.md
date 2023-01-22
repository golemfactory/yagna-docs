# Class: ExecutorConfig

[executor/config](../modules/executor_config.md).ExecutorConfig

## Table of contents

### Constructors

- [constructor](executor_config.ExecutorConfig.md#constructor)

### Properties

- [package](executor_config.ExecutorConfig.md#package)
- [maxParallelTasks](executor_config.ExecutorConfig.md#maxparalleltasks)
- [taskTimeout](executor_config.ExecutorConfig.md#tasktimeout)
- [budget](executor_config.ExecutorConfig.md#budget)
- [strategy](executor_config.ExecutorConfig.md#strategy)
- [subnetTag](executor_config.ExecutorConfig.md#subnettag)
- [payment](executor_config.ExecutorConfig.md#payment)
- [networkIp](executor_config.ExecutorConfig.md#networkip)
- [packageOptions](executor_config.ExecutorConfig.md#packageoptions)
- [logLevel](executor_config.ExecutorConfig.md#loglevel)
- [yagnaOptions](executor_config.ExecutorConfig.md#yagnaoptions)
- [logger](executor_config.ExecutorConfig.md#logger)
- [eventTarget](executor_config.ExecutorConfig.md#eventtarget)

## Constructors

### constructor

• **new ExecutorConfig**(`options`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `options` | [`ExecutorOptions`](../modules/executor_executor.md#executoroptions) |

#### Defined in

[yajsapi/executor/config.ts:39](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L39)

## Properties

### package

• `Readonly` **package**: `string` \| [`Package`](package_package.Package.md)

#### Defined in

[yajsapi/executor/config.ts:17](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L17)

___

### maxParallelTasks

• `Readonly` **maxParallelTasks**: `number`

#### Defined in

[yajsapi/executor/config.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L18)

___

### taskTimeout

• `Readonly` **taskTimeout**: `number`

#### Defined in

[yajsapi/executor/config.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L19)

___

### budget

• `Readonly` **budget**: `number`

#### Defined in

[yajsapi/executor/config.ts:20](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L20)

___

### strategy

• `Optional` `Readonly` **strategy**: [`MarketStrategy`](../interfaces/market_strategy.MarketStrategy.md)

#### Defined in

[yajsapi/executor/config.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L21)

___

### subnetTag

• `Readonly` **subnetTag**: `string`

#### Defined in

[yajsapi/executor/config.ts:22](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L22)

___

### payment

• `Readonly` **payment**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `driver` | `string` |
| `network` | `string` |

#### Defined in

[yajsapi/executor/config.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L23)

___

### networkIp

• `Optional` `Readonly` **networkIp**: `string`

#### Defined in

[yajsapi/executor/config.ts:24](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L24)

___

### packageOptions

• `Readonly` **packageOptions**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `engine?` | `string` |
| `repoUrl?` | `string` |
| `minMemGib?` | `number` |
| `minStorageGib?` | `number` |
| `minCpuThreads?` | `number` |
| `cores?` | `number` |
| `capabilities?` | `string`[] |

#### Defined in

[yajsapi/executor/config.ts:25](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L25)

___

### logLevel

• `Readonly` **logLevel**: `string`

#### Defined in

[yajsapi/executor/config.ts:34](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L34)

___

### yagnaOptions

• `Readonly` **yagnaOptions**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `apiKey` | `string` |
| `basePath` | `string` |

#### Defined in

[yajsapi/executor/config.ts:35](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L35)

___

### logger

• `Optional` `Readonly` **logger**: [`Logger`](../interfaces/utils_logger.Logger.md)

#### Defined in

[yajsapi/executor/config.ts:36](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L36)

___

### eventTarget

• `Readonly` **eventTarget**: `EventTarget`

#### Defined in

[yajsapi/executor/config.ts:37](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/executor/config.ts#L37)
