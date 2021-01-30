# storage/storageprovider

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [storage](../yajsapi-2/storage.md) / StorageProvider

## Class: StorageProvider

[storage](../yajsapi-2/storage.md).StorageProvider

### Hierarchy

* [_InputStorageProvider_](storage.inputstorageprovider.md)
* [_OutputStorageProvider_](storage.outputstorageprovider.md)

  ↳ **StorageProvider**

### Implemented by

* [_ComposedStorageProvider_](storage.composedstorageprovider.md)

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

+ **new StorageProvider**\(\): [_StorageProvider_](storage.storageprovider.md)

**Returns:** [_StorageProvider_](storage.storageprovider.md)

Inherited from: [OutputStorageProvider](storage.outputstorageprovider.md)

### Methods

#### new\_destination

▸ **new\_destination**\(`destination_file?`: _null_ \| _string_\): _Promise_&lt;[_Destination_](storage.destination.md)&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `destination_file` | _null_ \| _string_ | null |

**Returns:** _Promise_&lt;[_Destination_](storage.destination.md)&gt;

Inherited from: [OutputStorageProvider](storage.outputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:98](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L98)

#### upload\_bytes

▸ **upload\_bytes**\(`data`: _Buffer_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `data` | _Buffer_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:69](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L69)

#### upload\_file

▸ **upload\_file**\(`path`: _string_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `path` | _string_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L77)

#### upload\_stream

▸ **upload\_stream**\(`length`: _number_, `stream`: _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt;\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `length` | _number_ |
| `stream` | _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt; |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Inherited from: [InputStorageProvider](storage.inputstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L62)

