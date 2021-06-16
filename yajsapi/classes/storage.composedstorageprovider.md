[yajsapi](../README.md) / [Exports](../modules.md) / [storage](../modules/storage.md) / ComposedStorageProvider

# Class: ComposedStorageProvider

[storage](../modules/storage.md).ComposedStorageProvider

## Implements

- [StorageProvider](storage.storageprovider.md)

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

• **new ComposedStorageProvider**(`input_storage`, `output_storage`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `input_storage` | [InputStorageProvider](storage.inputstorageprovider.md) |
| `output_storage` | [OutputStorageProvider](storage.outputstorageprovider.md) |

#### Defined in

[yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L123)

## Properties

### \_input

• `Private` **\_input**: `any`

#### Defined in

[yajsapi/storage/index.ts:122](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L122)

___

### \_output

• `Private` **\_output**: `any`

#### Defined in

[yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L123)

## Methods

### new\_destination

▸ **new_destination**(`destination_file?`): `Promise`<[Destination](storage.destination.md)\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `destination_file` | ``null`` \| `string` | null |

#### Returns

`Promise`<[Destination](storage.destination.md)\>

#### Implementation of

StorageProvider.new\_destination

#### Defined in

[yajsapi/storage/index.ts:147](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L147)

___

### upload\_bytes

▸ **upload_bytes**(`data`): `Promise`<[Source](storage.source.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `data` | `Buffer` |

#### Returns

`Promise`<[Source](storage.source.md)\>

#### Implementation of

StorageProvider.upload\_bytes

#### Defined in

[yajsapi/storage/index.ts:132](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L132)

___

### upload\_file

▸ **upload_file**(`path`): `Promise`<[Source](storage.source.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `path` | `string` |

#### Returns

`Promise`<[Source](storage.source.md)\>

#### Implementation of

StorageProvider.upload\_file

#### Defined in

[yajsapi/storage/index.ts:143](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L143)

___

### upload\_stream

▸ **upload_stream**(`length`, `stream`): `Promise`<[Source](storage.source.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `length` | `number` |
| `stream` | `AsyncGenerator`<Buffer, any, unknown\> |

#### Returns

`Promise`<[Source](storage.source.md)\>

#### Implementation of

StorageProvider.upload\_stream

#### Defined in

[yajsapi/storage/index.ts:136](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L136)
