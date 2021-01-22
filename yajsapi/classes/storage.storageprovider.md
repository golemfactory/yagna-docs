[yajsapi](../README.md) / [Exports](../modules.md) / [storage](../modules/storage.md) / StorageProvider

# Class: StorageProvider

[storage](../modules/storage.md).StorageProvider

## Hierarchy

* [*InputStorageProvider*](storage.inputstorageprovider.md)

* [*OutputStorageProvider*](storage.outputstorageprovider.md)

  ↳ **StorageProvider**

## Implemented by

* [*ComposedStorageProvider*](storage.composedstorageprovider.md)

## Table of contents

### Constructors

- [constructor](storage.storageprovider.md#constructor)

### Methods

- [new\_destination](storage.storageprovider.md#new_destination)
- [upload\_bytes](storage.storageprovider.md#upload_bytes)
- [upload\_file](storage.storageprovider.md#upload_file)
- [upload\_stream](storage.storageprovider.md#upload_stream)

## Constructors

### constructor

\+ **new StorageProvider**(): [*StorageProvider*](storage.storageprovider.md)

**Returns:** [*StorageProvider*](storage.storageprovider.md)

Inherited from: [OutputStorageProvider](storage.outputstorageprovider.md)

## Methods

### new\_destination

▸ **new_destination**(`destination_file?`: *null* \| *string*): *Promise*<[*Destination*](storage.destination.md)\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`destination_file` | *null* \| *string* | null |

**Returns:** *Promise*<[*Destination*](storage.destination.md)\>

Inherited from: [OutputStorageProvider](storage.outputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:98](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L98)

___

### upload\_bytes

▸ **upload_bytes**(`data`: *Buffer*): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`data` | *Buffer* |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L69)

___

### upload\_file

▸ **upload_file**(`path`: *string*): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`path` | *string* |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L77)

___

### upload\_stream

▸ **upload_stream**(`length`: *number*, `stream`: *AsyncGenerator*<*Buffer*, *any*, *unknown*\>): *Promise*<[*Source*](storage.source.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`length` | *number* |
`stream` | *AsyncGenerator*<*Buffer*, *any*, *unknown*\> |

**Returns:** *Promise*<[*Source*](storage.source.md)\>

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L62)
