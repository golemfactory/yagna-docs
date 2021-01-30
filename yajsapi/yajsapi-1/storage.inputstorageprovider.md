# storage/inputstorageprovider

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [storage](../yajsapi-2/storage.md) / InputStorageProvider

## Class: InputStorageProvider

[storage](../yajsapi-2/storage.md).InputStorageProvider

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

Defined in: [yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L69)

#### upload\_file

▸ **upload\_file**\(`path`: _string_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `path` | _string_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L77)

#### upload\_stream

▸ **upload\_stream**\(`length`: _number_, `stream`: _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt;\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `length` | _number_ |
| `stream` | _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt; |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L62)

