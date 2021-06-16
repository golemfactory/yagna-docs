[yajsapi](../README.md) / [Exports](../modules.md) / [utils/queue](../modules/utils_queue.md) / default

# Class: default<T\>

[utils/queue](../modules/utils_queue.md).default

## Type parameters

| Name |
| :------ |
| `T` |

## Table of contents

### Constructors

- [constructor](utils_queue.default.md#constructor)

### Properties

- [\_\_new\_items](utils_queue.default.md#__new_items)
- [\_tasks](utils_queue.default.md#_tasks)

### Methods

- [close](utils_queue.default.md#close)
- [empty](utils_queue.default.md#empty)
- [get](utils_queue.default.md#get)
- [put](utils_queue.default.md#put)

## Constructors

### constructor

• **new default**<T\>(`list?`)

#### Type parameters

| Name |
| :------ |
| `T` |

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `list` | `any`[] | [] |

#### Defined in

[yajsapi/utils/queue.ts:7](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L7)

## Properties

### \_\_new\_items

• `Private` **\_\_new\_items**: `any`

#### Defined in

[yajsapi/utils/queue.ts:7](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L7)

___

### \_tasks

• `Private` **\_tasks**: `any`

#### Defined in

[yajsapi/utils/queue.ts:6](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L6)

## Methods

### close

▸ **close**(): `void`

#### Returns

`void`

#### Defined in

[yajsapi/utils/queue.ts:41](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L41)

___

### empty

▸ **empty**(): `boolean`

#### Returns

`boolean`

#### Defined in

[yajsapi/utils/queue.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L37)

___

### get

▸ **get**(): `Promise`<T\>

#### Returns

`Promise`<T\>

#### Defined in

[yajsapi/utils/queue.ts:24](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L24)

___

### put

▸ **put**(`item`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `item` | `T` |

#### Returns

`void`

#### Defined in

[yajsapi/utils/queue.ts:18](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/queue.ts#L18)
