# Class: InputStorageProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [storage](../modules/storage.md) / InputStorageProvider

## Class: InputStorageProvider

[storage](../modules/storage.md).InputStorageProvider

### Hierarchy

* **InputStorageProvider**

  ↳ [StorageProvider](storage.storageprovider.md)

### Table of contents

#### Constructors

* [constructor](storage.inputstorageprovider.md#constructor)

#### Methods

* [upload\_bytes](storage.inputstorageprovider.md#upload_bytes)
* [upload\_file](storage.inputstorageprovider.md#upload_file)
* [upload\_stream](storage.inputstorageprovider.md#upload_stream)

### Constructors

#### constructor

• **new InputStorageProvider**\(\)

### Methods

#### upload\_bytes

▸ **upload\_bytes**\(`data`\): `Promise`&lt;[Source](storage.source.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `data` | `Buffer` |

**Returns**

`Promise`&lt;[Source](storage.source.md)&gt;

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

**Defined in**

[yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/storage/index.ts#L62)

