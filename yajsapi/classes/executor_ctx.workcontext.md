# Class: WorkContext

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/ctx](../modules/executor_ctx.md) / WorkContext

## Class: WorkContext

[executor/ctx](../modules/executor_ctx.md).WorkContext

An object used to schedule commands to be sent to provider.

### Table of contents

#### Constructors

* [constructor](executor_ctx.workcontext.md#constructor)

#### Properties

* [\_emitter](executor_ctx.workcontext.md#_emitter)
* [\_id](executor_ctx.workcontext.md#_id)
* [\_pending\_steps](executor_ctx.workcontext.md#_pending_steps)
* [\_started](executor_ctx.workcontext.md#_started)
* [\_storage](executor_ctx.workcontext.md#_storage)

#### Methods

* [\_prepare](executor_ctx.workcontext.md#_prepare)
* [begin](executor_ctx.workcontext.md#begin)
* [commit](executor_ctx.workcontext.md#commit)
* [download\_file](executor_ctx.workcontext.md#download_file)
* [log](executor_ctx.workcontext.md#log)
* [run](executor_ctx.workcontext.md#run)
* [send\_file](executor_ctx.workcontext.md#send_file)
* [send\_json](executor_ctx.workcontext.md#send_json)
* [sign](executor_ctx.workcontext.md#sign)

### Constructors

#### constructor

• **new WorkContext**\(`ctx_id`, `storage`, `emitter?`\)

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `ctx_id` | `string` | `undefined` |
| `storage` | [StorageProvider](storage.storageprovider.md) | `undefined` |
| `emitter` | `null` \| [default](../interfaces/utils_callable.default.md)&lt;\[`StorageEvent`\], void&gt; | null |

**Defined in**

[yajsapi/executor/ctx.ts:289](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L289)

### Properties

#### \_emitter

• `Private` **\_emitter**: `null` \| [default](../interfaces/utils_callable.default.md)&lt;\[`StorageEvent`\], void&gt;

**Defined in**

[yajsapi/executor/ctx.ts:289](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L289)

#### \_id

• `Private` **\_id**: `any`

**Defined in**

[yajsapi/executor/ctx.ts:285](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L285)

#### \_pending\_steps

• `Private` **\_pending\_steps**: [Work](executor_ctx.work.md)\[\]

**Defined in**

[yajsapi/executor/ctx.ts:287](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L287)

#### \_started

• `Private` **\_started**: `boolean`

**Defined in**

[yajsapi/executor/ctx.ts:288](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L288)

#### \_storage

• `Private` **\_storage**: [StorageProvider](storage.storageprovider.md)

**Defined in**

[yajsapi/executor/ctx.ts:286](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L286)

### Methods

#### \_prepare

▸ **\_prepare**\(\): `void`

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:302](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L302)

#### begin

▸ **begin**\(\): `void`

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:308](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L308)

#### commit

▸ **commit**\(`__namedParameters?`\): [Work](executor_ctx.work.md)

Creates sequence of commands to be sent to provider.

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |
| `__namedParameters.timeout?` | `number` |

**Returns**

[Work](executor_ctx.work.md)

Work object \(the latter contains sequence commands added before calling this method\)

**Defined in**

[yajsapi/executor/ctx.ts:373](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L373)

#### download\_file

▸ **download\_file**\(`src_path`, `dst_path`\): `void`

Schedule downloading remote file from the provider.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `src_path` | `string` | remote \(provider\) path |
| `dst_path` | `string` | local \(requestor\) path |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:352](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L352)

#### log

▸ **log**\(`args`\): `void`

**Parameters**

| Name | Type |
| :--- | :--- |
| `args` | `any` |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:364](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L364)

#### run

▸ **run**\(`cmd`, `args?`, `env?`\): `void`

Schedule running a command.

**Parameters**

| Name | Type | Default value | Description |
| :--- | :--- | :--- | :--- |
| `cmd` | `string` | `undefined` | command to run on the provider, e.g. /my/dir/run.sh |
| `args?` | `Iterable` | `undefined` | command arguments, e.g. "input1.txt", "output1.txt" |
| `env` | `null` \| `object` | null | optional object with environmental variables |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:339](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L339)

#### send\_file

▸ **send\_file**\(`src_path`, `dst_path`\): `void`

Schedule sending file to the provider.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `src_path` | `string` | local \(requestor\) path |
| `dst_path` | `string` | remote \(provider\) path |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:327](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L327)

#### send\_json

▸ **send\_json**\(`json_path`, `data`\): `void`

Schedule sending JSON data to the provider.

**Parameters**

| Name | Type | Description |
| :--- | :--- | :--- |
| `json_path` | `string` | remote \(provider\) path |
| `data` | `Object` | object representing JSON data |

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:316](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L316)

#### sign

▸ **sign**\(\): `void`

**Returns**

`void`

**Defined in**

[yajsapi/executor/ctx.ts:359](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/ctx.ts#L359)

