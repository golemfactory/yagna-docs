# executor/ctx/work

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/ctx](../yajsapi-2/executor_ctx.md) / Work

## Class: Work

[executor/ctx](../yajsapi-2/executor_ctx.md).Work

### Hierarchy

* **Work**

### Table of contents

#### Constructors

* [constructor](executor_ctx.work.md#constructor)

#### Properties

* [attestation](executor_ctx.work.md#attestation)
* [output](executor_ctx.work.md#output)

#### Methods

* [post](executor_ctx.work.md#post)
* [prepare](executor_ctx.work.md#prepare)
* [register](executor_ctx.work.md#register)
* [timeout](executor_ctx.work.md#timeout)

### Constructors

#### constructor

+ **new Work**\(\): [_Work_](executor_ctx.work.md)

**Returns:** [_Work_](executor_ctx.work.md)

### Properties

#### attestation

• `Optional` **attestation**: _undefined_ \| _object_

Defined in: [yajsapi/executor/ctx.ts:50](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L50)

#### output

• **output**: _object_\[\]

Defined in: [yajsapi/executor/ctx.ts:49](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L49)

### Methods

#### post

▸ **post**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/ctx.ts:59](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L59)

#### prepare

▸ **prepare**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/ctx.ts:53](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L53)

#### register

▸ **register**\(`commands`: [_CommandContainer_](executor_ctx.commandcontainer.md)\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `commands` | [_CommandContainer_](executor_ctx.commandcontainer.md) |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L56)

#### timeout

▸ **timeout**\(\): _null_

**Returns:** _null_

Defined in: [yajsapi/executor/ctx.ts:61](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L61)

