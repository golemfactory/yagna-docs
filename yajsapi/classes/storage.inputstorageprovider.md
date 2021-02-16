# Class: InputStorageProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [storage](../modules/storage.md) / InputStorageProvider

## Class: InputStorageProvider

[storage](../modules/storage.md).InputStorageProvider

### Hierarchy

* **InputStorageProvider**

  ↳ [_StorageProvider_](storage.storageprovider.md)

### Table of contents

#### Constructors

* [constructor](storage.inputstorageprovider.md#constructor)

#### Methods

* [upload\_bytes](storage.inputstorageprovider.md#upload_bytes)
* [upload\_file](storage.inputstorageprovider.md#upload_file)
* [upload\_stream](storage.inputstorageprovider.md#upload_stream)

### Constructors

#### constructor

+ **new InputStorageProvider**\(\): [_InputStorageProvider_](storage.inputstorageprovider.md)

**Returns:** [_InputStorageProvider_](storage.inputstorageprovider.md)

### Methods

#### upload\_bytes

▸ **upload\_bytes**\(`data`: _Buffer_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `data` | _Buffer_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L69)

#### upload\_file

▸ **upload\_file**\(`path`: _string_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `path` | _string_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L77)

#### upload\_stream

▸ **upload\_stream**\(`length`: _number_, `stream`: _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt;\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `length` | _number_ |
| `stream` | _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt; |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L62)

