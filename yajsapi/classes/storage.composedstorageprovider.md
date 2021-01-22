[yajsapi](../README.md) / [Exports](../modules.md) / [storage](../modules/storage.md) / ComposedStorageProvider

# Class: ComposedStorageProvider

[storage](../modules/storage.md).ComposedStorageProvider

## Hierarchy

* **ComposedStorageProvider**

## Implements

* [*StorageProvider*](storage.storageprovider.md)

## Table of contents

### Constructors

- [constructor](storage.composedstorageprovider.md#constructor)

### Properties

- [\_input](storage.composedstorageprovider.md#_input)
- [\_output](storage.composedstorageprovider.md#_output)

### Methods

- [new\_destination](storage.composedstorageprovider.md#new_destination)
- [upload\_bytes](storage.composedstorageprovider.md#upload_bytes)
- [upload\_file](storage.composedstorageprovider.md#upload_file)
- [upload\_stream](storage.composedstorageprovider.md#upload_stream)

## Constructors

### constructor

\+ **new ComposedStorageProvider**(`input_storage`: [*InputStorageProvider*](storage.inputstorageprovider.md), `output_storage`: [*OutputStorageProvider*](storage.outputstorageprovider.md)): [*ComposedStorageProvider*](storage.composedstorageprovider.md)

#### Parameters:

Name | Type |
------ | ------ |
`input_storage` | [*InputStorageProvider*](storage.inputstorageprovider.md) |
`output_storage` | [*OutputStorageProvider*](storage.outputstorageprovider.md) |

**Returns:** [*ComposedStorageProvider*](storage.composedstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L123)

## Properties

### \_input

• `Private` **\_input**: *any*

Defined in: [yajsapi/storage/index.ts:122](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L122)

___

### \_output

• `Private` **\_output**: *any*

Defined in: [yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L123)

## Methods

### new\_destination

▸ **new_destination**(`destination_file?`: *null* \| *string*): *Promise*<[*Destination*](storage.destination.md)\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`destination_file` | *null* \| *string* | null |

**Returns:** *Promise*<[*Destination*](storage.destination.md)\>

Defined in: [yajsapi/storage/index.ts:147](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L147)

___

### upload\_bytes

▸ **upload_bytes**(`data`: *Buffer*): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`data` | *Buffer* |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Defined in: [yajsapi/storage/index.ts:132](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L132)

___

### upload\_file

▸ **upload_file**(`path`: *string*): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`path` | *string* |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Defined in: [yajsapi/storage/index.ts:143](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L143)

___

### upload\_stream

▸ **upload_stream**(`length`: *number*, `stream`: *AsyncGenerator*<*Buffer*, *any*, *unknown*\>): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`length` | *number* |
`stream` | *AsyncGenerator*<*Buffer*, *any*, *unknown*\> |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Defined in: [yajsapi/storage/index.ts:136](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L136)
