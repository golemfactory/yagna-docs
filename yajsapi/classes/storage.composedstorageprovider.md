# Class: ComposedStorageProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [storage](../modules/storage.md) / ComposedStorageProvider

## Class: ComposedStorageProvider

[storage](../modules/storage.md).ComposedStorageProvider

### Hierarchy

* **ComposedStorageProvider**

### Implements

* [_StorageProvider_](storage.storageprovider.md)

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

* **new ComposedStorageProvider**\(`input_storage`: [_InputStorageProvider_](storage.inputstorageprovider.md), `output_storage`: [_OutputStorageProvider_](storage.outputstorageprovider.md)\): [_ComposedStorageProvider_](storage.composedstorageprovider.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `input_storage` | [_InputStorageProvider_](storage.inputstorageprovider.md) |
| `output_storage` | [_OutputStorageProvider_](storage.outputstorageprovider.md) |

**Returns:** [_ComposedStorageProvider_](storage.composedstorageprovider.md)

Defined in: [yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L123)

### Properties

#### \_input

• `Private` **\_input**: _any_

Defined in: [yajsapi/storage/index.ts:122](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L122)

#### \_output

• `Private` **\_output**: _any_

Defined in: [yajsapi/storage/index.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L123)

### Methods

#### new\_destination

▸ **new\_destination**\(`destination_file?`: _null_ \| _string_\): _Promise_&lt;[_Destination_](storage.destination.md)&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `destination_file` | _null_ \| _string_ | null |

**Returns:** _Promise_&lt;[_Destination_](storage.destination.md)&gt;

Defined in: [yajsapi/storage/index.ts:147](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L147)

#### upload\_bytes

▸ **upload\_bytes**\(`data`: _Buffer_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `data` | _Buffer_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:132](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L132)

#### upload\_file

▸ **upload\_file**\(`path`: _string_\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `path` | _string_ |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:143](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L143)

#### upload\_stream

▸ **upload\_stream**\(`length`: _number_, `stream`: _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt;\): _Promise_&lt;[_Source_](storage.source.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `length` | _number_ |
| `stream` | _AsyncGenerator_&lt;_Buffer_, _any_, _unknown_&gt; |

**Returns:** _Promise_&lt;[_Source_](storage.source.md)&gt;

Defined in: [yajsapi/storage/index.ts:136](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/storage/index.ts#L136)

