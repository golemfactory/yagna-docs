[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / WorkerFinished

# Class: WorkerFinished

[executor/events](../modules/executor_events.md).WorkerFinished

## Hierarchy

- `AgreementEvent`

  ↳ **WorkerFinished**

## Table of contents

### Constructors

- [constructor](executor_events.workerfinished.md#constructor)

### Properties

- [agr\_id](executor_events.workerfinished.md#agr_id)
- [exception](executor_events.workerfinished.md#exception)

### Methods

- [extract\_exc\_info](executor_events.workerfinished.md#extract_exc_info)

## Constructors

### constructor

• **new WorkerFinished**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

AgreementEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:264](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L264)

## Properties

### agr\_id

• `Optional` **agr\_id**: `string`

#### Inherited from

AgreementEvent.agr\_id

#### Defined in

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

___

### exception

• `Optional` **exception**: ``null`` \| `Error` = null

#### Defined in

[yajsapi/executor/events.ts:264](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L264)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

#### Returns

[`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

#### Overrides

AgreementEvent.extract\_exc\_info

#### Defined in

[yajsapi/executor/events.ts:272](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L272)
