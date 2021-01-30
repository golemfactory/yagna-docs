# utils/asyncwrapper.default

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [utils/asyncWrapper](../yajsapi-2/utils_asyncwrapper.md) / default

## Class: default

[utils/asyncWrapper](../yajsapi-2/utils_asyncwrapper.md).default

### Hierarchy

* **default**

### Table of contents

#### Constructors

* [constructor](utils_asyncwrapper.default.md#constructor)

#### Properties

* [\_args\_buffer](utils_asyncwrapper.default.md#_args_buffer)
* [\_cancellationToken](utils_asyncwrapper.default.md#_cancellationtoken)
* [\_loop](utils_asyncwrapper.default.md#_loop)
* [\_task](utils_asyncwrapper.default.md#_task)
* [\_wrapped](utils_asyncwrapper.default.md#_wrapped)

#### Methods

* [\_worker](utils_asyncwrapper.default.md#_worker)
* [async\_call](utils_asyncwrapper.default.md#async_call)
* [done](utils_asyncwrapper.default.md#done)
* [ready](utils_asyncwrapper.default.md#ready)

### Constructors

#### constructor

+ **new default**\(`wrapped`: [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;_any_, _any_&gt;, `event_loop?`: _any_, `cancellationToken`: _any_\): [_default_](utils_asyncwrapper.default.md)

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `wrapped` | [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;_any_, _any_&gt; | - |
| `event_loop` | _any_ | null |
| `cancellationToken` | _any_ | - |

**Returns:** [_default_](utils_asyncwrapper.default.md)

Defined in: [yajsapi/utils/asyncWrapper.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L8)

### Properties

#### \_args\_buffer

• `Private` **\_args\_buffer**: [_default_](utils_queue.default.md)&lt;_any_&gt;

Defined in: [yajsapi/utils/asyncWrapper.ts:5](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L5)

#### \_cancellationToken

• `Private` **\_cancellationToken**: _any_

Defined in: [yajsapi/utils/asyncWrapper.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L8)

#### \_loop

• `Private` **\_loop**: _any_

Defined in: [yajsapi/utils/asyncWrapper.ts:7](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L7)

#### \_task

• `Private` **\_task**: _any_

Defined in: [yajsapi/utils/asyncWrapper.ts:6](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L6)

#### \_wrapped

• `Private` **\_wrapped**: [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;_any_, _any_&gt;

Defined in: [yajsapi/utils/asyncWrapper.ts:4](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L4)

### Methods

#### \_worker

▸ **\_worker**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/utils/asyncWrapper.ts:22](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L22)

#### async\_call

▸ **async\_call**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/utils/asyncWrapper.ts:44](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L44)

#### done

▸ **done**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/utils/asyncWrapper.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L37)

#### ready

▸ **ready**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/utils/asyncWrapper.ts:31](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncWrapper.ts#L31)

