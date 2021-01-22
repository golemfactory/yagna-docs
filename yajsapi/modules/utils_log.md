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

• `Const` **default**: *Logger*

Defined in: [yajsapi/utils/log.ts:78](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/log.ts#L78)

Defined in: [yajsapi/utils/index.ts:25](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/index.ts#L25)

## Functions

### changeLogLevel

▸ `Const`**changeLogLevel**(`level`: *string*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`level` | *string* |

**Returns:** *void*

Defined in: [yajsapi/utils/log.ts:344](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/log.ts#L344)

___

### logSummary

▸ **logSummary**(`wrapped_emitter?`: [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](../classes/executor_events.yaevent.md)], *void*\> \| *null*): *function*

#### Parameters:

Name | Type |
------ | ------ |
`wrapped_emitter?` | [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](../classes/executor_events.yaevent.md)], *void*\> \| *null* |

**Returns:** *function*

Defined in: [yajsapi/utils/log.ts:328](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/log.ts#L328)
