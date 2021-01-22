[yajsapi](../README.md) / [Exports](../modules.md) / [utils/asyncWrapper](../modules/utils_asyncwrapper.md) / default

# Class: default

[utils/asyncWrapper](../modules/utils_asyncwrapper.md).default

## Hierarchy

* **default**

## Table of contents

### Constructors

- [constructor](utils_asyncwrapper.default.md#constructor)

### Properties

- [\_args\_buffer](utils_asyncwrapper.default.md#_args_buffer)
- [\_cancellationToken](utils_asyncwrapper.default.md#_cancellationtoken)
- [\_loop](utils_asyncwrapper.default.md#_loop)
- [\_task](utils_asyncwrapper.default.md#_task)
- [\_wrapped](utils_asyncwrapper.default.md#_wrapped)

### Methods

- [\_worker](utils_asyncwrapper.default.md#_worker)
- [async\_call](utils_asyncwrapper.default.md#async_call)
- [done](utils_asyncwrapper.default.md#done)
- [ready](utils_asyncwrapper.default.md#ready)

## Constructors

### constructor

\+ **new default**(`wrapped`: [*default*](../interfaces/utils_callable.default.md)<*any*, *any*\>, `event_loop?`: *any*, `cancellationToken`: *any*): [*default*](utils_asyncwrapper.default.md)

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`wrapped` | [*default*](../interfaces/utils_callable.default.md)<*any*, *any*\> | - |
`event_loop` | *any* | null |
`cancellationToken` | *any* | - |

**Returns:** [*default*](utils_asyncwrapper.default.md)

Defined in: [yajsapi/utils/asyncWrapper.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L8)

## Properties

### \_args\_buffer

• `Private` **\_args\_buffer**: [*default*](utils_queue.default.md)<*any*\>

Defined in: [yajsapi/utils/asyncWrapper.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L5)

___

### \_cancellationToken

• `Private` **\_cancellationToken**: *any*

Defined in: [yajsapi/utils/asyncWrapper.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L8)

___

### \_loop

• `Private` **\_loop**: *any*

Defined in: [yajsapi/utils/asyncWrapper.ts:7](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L7)

___

### \_task

• `Private` **\_task**: *any*

Defined in: [yajsapi/utils/asyncWrapper.ts:6](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L6)

___

### \_wrapped

• `Private` **\_wrapped**: [*default*](../interfaces/utils_callable.default.md)<*any*, *any*\>

Defined in: [yajsapi/utils/asyncWrapper.ts:4](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L4)

## Methods

### \_worker

▸ **_worker**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/utils/asyncWrapper.ts:22](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L22)

___

### async\_call

▸ **async_call**(): *void*

**Returns:** *void*

Defined in: [yajsapi/utils/asyncWrapper.ts:44](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L44)

___

### done

▸ **done**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/utils/asyncWrapper.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L37)

___

### ready

▸ **ready**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/utils/asyncWrapper.ts:31](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L31)
