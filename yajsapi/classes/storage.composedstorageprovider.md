# Class: ComposedStorageProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [storage](../modules/storage.md) / ComposedStorageProvider

## Class: ComposedStorageProvider

[storage](../modules/storage.md).ComposedStorageProvider

### Implements

* [StorageProvider](storage.storageprovider.md)

### Table of contents

#### Constructors

* [constructor](storage.composedstorageprovider.md#constructor)

#### Properties

* [\_input](storage.composedstorageprovider.md#_input)
* [\_output](storage.composedstorageprovider.md#_output)

#### Methods

* [new\_destination](storage.composedstorageprovider.md#new_destination)
* [upload\_bytes](storage.composedstorageprovider.md#upload_bytes)
* [upload\_file](storage.composedstorageprovider.md#upload_file)
* [upload\_stream](storage.composedstorageprovider.md#upload_stream)

### Constructors

#### constructor

• **new ComposedStorageProvider**\(`input_storage`, `output_storage`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `input_storage` | [InputStorageProvider](storage.inputstorageprovider.md) |
| `output_storage` | [OutputStorageProvider](storage.outputstorageprovider.md) |

**Defined in**

[yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L123)

### Properties

#### \_input

• `Private` **\_input**: `any`

**Defined in**

[yajsapi/storage/index.ts:122](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L122)

#### \_output

• `Private` **\_output**: `any`

**Defined in**

[yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L123)

### Methods

#### new\_destination

▸ **new\_destination**\(`destination_file?`\): `Promise`&lt;[Destination](storage.destination.md)&gt;

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `destination_file` | `null` \| `string` | null |

**Returns**

`Promise`&lt;[Destination](storage.destination.md)&gt;

**Implementation of**

StorageProvider.new\_destination

**Defined in**

[yajsapi/storage/index.ts:147](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L147)

#### upload\_bytes

▸ **upload\_bytes**\(`data`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `data` | `Buffer` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Implementation of**

StorageProvider.upload\_bytes

**Defined in**

[yajsapi/storage/index.ts:132](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L132)

#### upload\_file

▸ **upload\_file**\(`path`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `path` | `string` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Implementation of**

StorageProvider.upload\_file

**Defined in**

[yajsapi/storage/index.ts:143](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L143)

#### upload\_stream

▸ **upload\_stream**\(`length`, `stream`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `length` | `number` |
| `stream` | `AsyncGenerator` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Implementation of**

StorageProvider.upload\_stream

**Defined in**

[yajsapi/storage/index.ts:136](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L136)

