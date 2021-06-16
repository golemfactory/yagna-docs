# Class: Work

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/ctx](../modules/executor_ctx.md) / Work

## Class: Work

[executor/ctx](../modules/executor_ctx.md).Work

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

• **new Work**\(\)

### Properties

#### attestation

• `Optional` **attestation**: `object`

**Defined in**

[yajsapi/executor/ctx.ts:50](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L50)

#### output

• **output**: `object`\[\] = \[\]

**Defined in**

[yajsapi/executor/ctx.ts:49](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L49)

### Methods

#### post

▸ **post**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/ctx.ts:59](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L59)

#### prepare

▸ **prepare**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/ctx.ts:53](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L53)

#### register

▸ **register**\(`commands`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `commands` | [CommandContainer](executor_ctx.commandcontainer.md) |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:56](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L56)

#### timeout

▸ **timeout**\(\): `null`

**Returns**

`null`

**Defined in**

[yajsapi/executor/ctx.ts:61](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L61)

