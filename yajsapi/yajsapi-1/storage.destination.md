# storage/destination

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [storage](../yajsapi-2/storage.md) / Destination

## Class: Destination

[storage](../yajsapi-2/storage.md).Destination

### Hierarchy

* **Destination**

### Table of contents

#### Constructors

* [constructor](storage.destination.md#constructor)

#### Methods

* [download\_file](storage.destination.md#download_file)
* [download\_stream](storage.destination.md#download_stream)
* [upload\_url](storage.destination.md#upload_url)

### Constructors

#### constructor

+ **new Destination**\(\): [_Destination_](storage.destination.md)

**Returns:** [_Destination_](storage.destination.md)

### Methods

#### download\_file

▸ **download\_file**\(`destination_file`: _string_\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `destination_file` | _string_ |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/storage/index.ts:45](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L45)

#### download\_stream

▸ **download\_stream**\(\): _Promise_&lt;[_Content_](storage.content.md)&gt;

**Returns:** _Promise_&lt;[_Content_](storage.content.md)&gt;

Defined in: [yajsapi/storage/index.ts:41](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L41)

#### upload\_url

▸ **upload\_url**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/storage/index.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L37)

