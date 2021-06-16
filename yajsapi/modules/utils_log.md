[yajsapi](../README.md) / [Exports](../modules.md) / utils/log

# Module: utils/log

## Table of contents

### Variables

- [default](utils_log.md#default)

### Functions

- [changeLogLevel](utils_log.md#changeloglevel)
- [logSummary](utils_log.md#logsummary)

## Variables

### default

• `Const` **default**: `Logger`

#### Defined in

[yajsapi/utils/log.ts:74](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/log.ts#L74)

## Functions

### changeLogLevel

▸ `Const` **changeLogLevel**(`level`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `level` | `string` |

#### Returns

`void`

#### Defined in

[yajsapi/utils/log.ts:351](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/log.ts#L351)

___

### logSummary

▸ **logSummary**(`wrapped_emitter?`): (`event`: [YaEvent](../classes/executor_events.yaevent.md)) => `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `wrapped_emitter?` | [default](../interfaces/utils_callable.default.md)<[[YaEvent](../classes/executor_events.yaevent.md)], void\> \| ``null`` |

#### Returns

`fn`

▸ (`event`): `void`

##### Parameters

| Name | Type |
| :------ | :------ |
| `event` | [YaEvent](../classes/executor_events.yaevent.md) |

##### Returns

`void`

#### Defined in

[yajsapi/utils/log.ts:344](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/log.ts#L344)
