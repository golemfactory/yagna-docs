[yajsapi](../README.md) / [Exports](../modules.md) / [storage](../modules/storage.md) / Destination

# Class: Destination

[storage](../modules/storage.md).Destination

## Hierarchy

* **Destination**

## Table of contents

### Constructors

- [constructor](storage.destination.md#constructor)

### Methods

- [download\_file](storage.destination.md#download_file)
- [download\_stream](storage.destination.md#download_stream)
- [upload\_url](storage.destination.md#upload_url)

## Constructors

### constructor

\+ **new Destination**(): [*Destination*](storage.destination.md)

**Returns:** [*Destination*](storage.destination.md)

## Methods

### download\_file

▸ **download_file**(`destination_file`: *string*): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`destination_file` | *string* |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/storage/index.ts:45](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L45)

___

### download\_stream

▸ **download_stream**(): *Promise*<[*Content*](storage.content.md)\>

**Returns:** *Promise*<[*Content*](storage.content.md)\>

Defined in: [yajsapi/storage/index.ts:41](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L41)

___

### upload\_url

▸ **upload_url**(): *string*

**Returns:** *string*

Defined in: [yajsapi/storage/index.ts:37](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/storage/index.ts#L37)
