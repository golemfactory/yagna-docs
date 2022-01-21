# Class: StorageProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [storage](../modules/storage.md) / StorageProvider

## Class: StorageProvider

[storage](../modules/storage.md).StorageProvider

### Hierarchy

* [InputStorageProvider](storage.inputstorageprovider.md)
* [OutputStorageProvider](storage.outputstorageprovider.md)

  ↳ **StorageProvider**

### Implemented by

* [ComposedStorageProvider](storage.composedstorageprovider.md)

### Table of contents

#### Constructors

* [constructor](storage.storageprovider.md#constructor)

#### Methods

* [new\_destination](storage.storageprovider.md#new_destination)
* [upload\_bytes](storage.storageprovider.md#upload_bytes)
* [upload\_file](storage.storageprovider.md#upload_file)
* [upload\_stream](storage.storageprovider.md#upload_stream)

### Constructors

#### constructor

• **new StorageProvider**\(\)

**Inherited from**

[OutputStorageProvider](storage.outputstorageprovider.md).[constructor](storage.outputstorageprovider.md#constructor)

### Methods

#### new\_destination

▸ **new\_destination**\(`destination_file?`\): `Promise`&lt;[Destination](storage.destination.md)&gt;

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `destination_file` | `null` \| `string` | null |

**Returns**

`Promise`&lt;[Destination](storage.destination.md)&gt;

**Inherited from**

[OutputStorageProvider](storage.outputstorageprovider.md).[new\_destination](storage.outputstorageprovider.md#new_destination)

**Defined in**

[yajsapi/storage/index.ts:98](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L98)

#### upload\_bytes

▸ **upload\_bytes**\(`data`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `data` | `Buffer` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Inherited from**

[InputStorageProvider](storage.inputstorageprovider.md).[upload\_bytes](storage.inputstorageprovider.md#upload_bytes)

**Defined in**

[yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L69)

#### upload\_file

▸ **upload\_file**\(`path`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `path` | `string` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Inherited from**

[InputStorageProvider](storage.inputstorageprovider.md).[upload\_file](storage.inputstorageprovider.md#upload_file)

**Defined in**

[yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L77)

#### upload\_stream

▸ **upload\_stream**\(`length`, `stream`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `length` | `number` |
| `stream` | `AsyncGenerator` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

**Inherited from**

[InputStorageProvider](storage.inputstorageprovider.md).[upload\_stream](storage.inputstorageprovider.md#upload_stream)

**Defined in**

[yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L62)

