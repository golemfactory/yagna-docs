[yajsapi](../README.md) / [Exports](../modules.md) / [executor/smartq](../modules/executor_smartq.md) / Consumer

# Class: Consumer<Item\>

[executor/smartq](../modules/executor_smartq.md).Consumer

## Type parameters

| Name |
| :------ |
| `Item` |

## Table of contents

### Constructors

- [constructor](executor_smartq.consumer.md#constructor)

### Properties

- [\_fetched](executor_smartq.consumer.md#_fetched)
- [\_queue](executor_smartq.consumer.md#_queue)

### Methods

- [[Symbol.asyncIterator]](executor_smartq.consumer.md#[symbol.asynciterator])
- [done](executor_smartq.consumer.md#done)
- [last\_item](executor_smartq.consumer.md#last_item)
- [ready](executor_smartq.consumer.md#ready)

## Constructors

### constructor

• **new Consumer**<Item\>(`queue`)

#### Type parameters

| Name |
| :------ |
| `Item` |

#### Parameters

| Name | Type |
| :------ | :------ |
| `queue` | [SmartQueue](executor_smartq.smartqueue.md)<Item\> |

#### Defined in

[yajsapi/executor/smartq.ts:169](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L169)

## Properties

### \_fetched

• `Private` `Optional` **\_fetched**: ``null`` \| [Handle](executor_smartq.handle.md)<Item\>

#### Defined in

[yajsapi/executor/smartq.ts:169](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L169)

___

### \_queue

• `Private` **\_queue**: `any`

#### Defined in

[yajsapi/executor/smartq.ts:168](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L168)

## Methods

### [Symbol.asyncIterator]

▸ **[Symbol.asyncIterator]**(): `AsyncGenerator`<[Handle](executor_smartq.handle.md)<Item\>, any, any\>

#### Returns

`AsyncGenerator`<[Handle](executor_smartq.handle.md)<Item\>, any, any\>

#### Defined in

[yajsapi/executor/smartq.ts:189](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L189)

___

### done

▸ **done**(): ``null``

#### Returns

``null``

#### Defined in

[yajsapi/executor/smartq.ts:180](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L180)

___

### last\_item

▸ **last_item**(): ``null`` \| `Item`

#### Returns

``null`` \| `Item`

#### Defined in

[yajsapi/executor/smartq.ts:185](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L185)

___

### ready

▸ **ready**(): [Consumer](executor_smartq.consumer.md)<Item\>

#### Returns

[Consumer](executor_smartq.consumer.md)<Item\>

#### Defined in

[yajsapi/executor/smartq.ts:176](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L176)
