[yajsapi](../README.md) / [Exports](../modules.md) / [storage](../modules/storage.md) / InputStorageProvider

# Class: InputStorageProvider

[storage](../modules/storage.md).InputStorageProvider

## Hierarchy

- **InputStorageProvider**

  ↳ [StorageProvider](storage.storageprovider.md)

## Table of contents

### Constructors

- [constructor](storage.inputstorageprovider.md#constructor)

### Methods

- [upload\_bytes](storage.inputstorageprovider.md#upload_bytes)
- [upload\_file](storage.inputstorageprovider.md#upload_file)
- [upload\_stream](storage.inputstorageprovider.md#upload_stream)

## Constructors

### constructor

• **new InputStorageProvider**()

## Methods

### upload\_bytes

▸ **upload_bytes**(`data`): `Promise`<[Source](storage.source.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `data` | `Buffer` |

#### Returns

`Promise`<[Source](storage.source.md)\>

#### Defined in

[yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L69)

___

### upload\_file

▸ **upload_file**(`path`): `Promise`<[Source](storage.source.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `path` | `string` |

#### Returns

`Promise`<[Source](storage.source.md)\>

#### Defined in

[yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L77)

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

#### Defined in

[yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L62)
