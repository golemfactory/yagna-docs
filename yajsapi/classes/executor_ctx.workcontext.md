[yajsapi](../README.md) / [Exports](../modules.md) / [executor/ctx](../modules/executor_ctx.md) / WorkContext

# Class: WorkContext

[executor/ctx](../modules/executor_ctx.md).WorkContext

An object used to schedule commands to be sent to provider.

## Hierarchy

* **WorkContext**

## Table of contents

### Constructors

- [constructor](executor_ctx.workcontext.md#constructor)

### Properties

- [\_emitter](executor_ctx.workcontext.md#_emitter)
- [\_id](executor_ctx.workcontext.md#_id)
- [\_pending\_steps](executor_ctx.workcontext.md#_pending_steps)
- [\_started](executor_ctx.workcontext.md#_started)
- [\_storage](executor_ctx.workcontext.md#_storage)

### Methods

- [\_prepare](executor_ctx.workcontext.md#_prepare)
- [begin](executor_ctx.workcontext.md#begin)
- [commit](executor_ctx.workcontext.md#commit)
- [download\_file](executor_ctx.workcontext.md#download_file)
- [log](executor_ctx.workcontext.md#log)
- [run](executor_ctx.workcontext.md#run)
- [send\_file](executor_ctx.workcontext.md#send_file)
- [send\_json](executor_ctx.workcontext.md#send_json)
- [sign](executor_ctx.workcontext.md#sign)

## Constructors

### constructor

\+ **new WorkContext**(`ctx_id`: *string*, `storage`: [*StorageProvider*](storage.storageprovider.md), `emitter?`: *null* \| [*default*](../interfaces/utils_callable.default.md)<[StorageEvent], *void*\>): [*WorkContext*](executor_ctx.workcontext.md)

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`ctx_id` | *string* | - |
`storage` | [*StorageProvider*](storage.storageprovider.md) | - |
`emitter` | *null* \| [*default*](../interfaces/utils_callable.default.md)<[StorageEvent], *void*\> | null |

**Returns:** [*WorkContext*](executor_ctx.workcontext.md)

Defined in: [yajsapi/executor/ctx.ts:284](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L284)

## Properties

### \_emitter

• `Private` **\_emitter**: *null* \| [*default*](../interfaces/utils_callable.default.md)<[StorageEvent], *void*\>

Defined in: [yajsapi/executor/ctx.ts:284](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L284)

___

### \_id

• `Private` **\_id**: *any*

Defined in: [yajsapi/executor/ctx.ts:280](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L280)

___

### \_pending\_steps

• `Private` **\_pending\_steps**: [*Work*](executor_ctx.work.md)[]

Defined in: [yajsapi/executor/ctx.ts:282](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L282)

___

### \_started

• `Private` **\_started**: *boolean*

Defined in: [yajsapi/executor/ctx.ts:283](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L283)

___

### \_storage

• `Private` **\_storage**: [*StorageProvider*](storage.storageprovider.md)

Defined in: [yajsapi/executor/ctx.ts:281](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L281)

## Methods

### \_prepare

▸ **_prepare**(): *void*

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:297](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L297)

___

### begin

▸ **begin**(): *void*

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:303](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L303)

___

### commit

▸ **commit**(`__namedParameters`: { `timeout?`: *undefined* \| *number*  }): [*Work*](executor_ctx.work.md)

Creates sequence of commands to be sent to provider.

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | { `timeout?`: *undefined* \| *number*  } |

**Returns:** [*Work*](executor_ctx.work.md)

Work object (the latter contains sequence commands added before calling this method)

Defined in: [yajsapi/executor/ctx.ts:368](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L368)

___

### download\_file

▸ **download_file**(`src_path`: *string*, `dst_path`: *string*): *void*

Schedule downloading remote file from the provider.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`src_path` | *string* | remote (provider) path   |
`dst_path` | *string* | local (requestor) path    |

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:347](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L347)

___

### log

▸ **log**(`args`: *any*): *void*

#### Parameters:

Name | Type |
------ | ------ |
`args` | *any* |

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:359](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L359)

___

### run

▸ **run**(`cmd`: *string*, `args?`: *Iterable*<*string*\>, `env?`: *null* \| *object*): *void*

Schedule running a command.

#### Parameters:

Name | Type | Default value | Description |
------ | ------ | ------ | ------ |
`cmd` | *string* | - | command to run on the provider, e.g. /my/dir/run.sh   |
`args?` | *Iterable*<*string*\> | - | command arguments, e.g. "input1.txt", "output1.txt"   |
`env` | *null* \| *object* | null | optional object with environmental variables    |

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:334](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L334)

___

### send\_file

▸ **send_file**(`src_path`: *string*, `dst_path`: *string*): *void*

Schedule sending file to the provider.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`src_path` | *string* | local (requestor) path   |
`dst_path` | *string* | remote (provider) path    |

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:322](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L322)

___

### send\_json

▸ **send_json**(`json_path`: *string*, `data`: {}): *void*

Schedule sending JSON data to the provider.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`json_path` | *string* | remote (provider) path   |
`data` | {} | object representing JSON data    |

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:311](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L311)

___

### sign

▸ **sign**(): *void*

**Returns:** *void*

Defined in: [yajsapi/executor/ctx.ts:354](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/ctx.ts#L354)
