# Class: WorkContext

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/ctx](../modules/executor_ctx.md) / WorkContext

## Class: WorkContext

[executor/ctx](../modules/executor_ctx.md).WorkContext

An object used to schedule commands to be sent to provider.

### Hierarchy

* **WorkContext**

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

* **new WorkContext**\(`ctx_id`: _string_, `storage`: [_StorageProvider_](storage.storageprovider.md), `emitter?`: _null_ \| [_default_](../interface/utils_callable.default.md)&lt;\[StorageEvent\], _void_&gt;\): [_WorkContext_](executor_ctx.workcontext.md)

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `ctx_id` | _string_ | - |
| `storage` | [_StorageProvider_](storage.storageprovider.md) | - |
| `emitter` | _null_ \| [_default_](../interface/utils_callable.default.md)&lt;\[StorageEvent\], _void_&gt; | null |

**Returns:** [_WorkContext_](executor_ctx.workcontext.md)

Defined in: [yajsapi/executor/ctx.ts:284](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L284)

### Properties

#### \_emitter

• `Private` **\_emitter**: _null_ \| [_default_](../interface/utils_callable.default.md)&lt;\[StorageEvent\], _void_&gt;

Defined in: [yajsapi/executor/ctx.ts:284](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L284)

#### \_id

• `Private` **\_id**: _any_

Defined in: [yajsapi/executor/ctx.ts:280](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L280)

#### \_pending\_steps

• `Private` **\_pending\_steps**: [_Work_](executor_ctx.work.md)\[\]

Defined in: [yajsapi/executor/ctx.ts:282](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L282)

#### \_started

• `Private` **\_started**: _boolean_

Defined in: [yajsapi/executor/ctx.ts:283](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L283)

#### \_storage

• `Private` **\_storage**: [_StorageProvider_](storage.storageprovider.md)

Defined in: [yajsapi/executor/ctx.ts:281](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L281)

### Methods

#### \_prepare

▸ **\_prepare**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:297](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L297)

#### begin

▸ **begin**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:303](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L303)

#### commit

▸ **commit**\(`__namedParameters`: { `timeout?`: _undefined_ \| _number_ }\): [_Work_](executor_ctx.work.md)

Creates sequence of commands to be sent to provider.

**Parameters:**

• **\_\_namedParameters**: _object_

| Name | Type |
| :--- | :--- |
| `timeout?` | _undefined_ \| _number_ |

**Returns:** [_Work_](executor_ctx.work.md)

Work object \(the latter contains sequence commands added before calling this method\)

Defined in: [yajsapi/executor/ctx.ts:368](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L368)

#### download\_file

▸ **download\_file**\(`src_path`: _string_, `dst_path`: _string_\): _void_

Schedule downloading remote file from the provider.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `src_path` | _string_ | remote \(provider\) path |
| `dst_path` | _string_ | local \(requestor\) path |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:347](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L347)

#### log

▸ **log**\(`args`: _any_\): _void_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `args` | _any_ |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:359](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L359)

#### run

▸ **run**\(`cmd`: _string_, `args?`: _Iterable_&lt;_string_&gt;, `env?`: _null_ \| _object_\): _void_

Schedule running a command.

**Parameters:**

| Name | Type | Default value | Description |
| :--- | :--- | :--- | :--- |
| `cmd` | _string_ | - | command to run on the provider, e.g. /my/dir/run.sh |
| `args?` | _Iterable_&lt;_string_&gt; | - | command arguments, e.g. "input1.txt", "output1.txt" |
| `env` | _null_ \| _object_ | null | optional object with environmental variables |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:334](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L334)

#### send\_file

▸ **send\_file**\(`src_path`: _string_, `dst_path`: _string_\): _void_

Schedule sending file to the provider.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `src_path` | _string_ | local \(requestor\) path |
| `dst_path` | _string_ | remote \(provider\) path |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:322](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L322)

#### send\_json

▸ **send\_json**\(`json_path`: _string_, `data`: {}\): _void_

Schedule sending JSON data to the provider.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `json_path` | _string_ | remote \(provider\) path |
| `data` | {} | object representing JSON data |

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:311](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L311)

#### sign

▸ **sign**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/executor/ctx.ts:354](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/ctx.ts#L354)

