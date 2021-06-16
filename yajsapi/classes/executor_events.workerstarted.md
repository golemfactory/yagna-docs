[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / WorkerStarted

# Class: WorkerStarted

[executor/events](../modules/executor_events.md).WorkerStarted

## Hierarchy

- `AgreementEvent`

  ↳ **WorkerStarted**

## Table of contents

### Constructors

- [constructor](executor_events.workerstarted.md#constructor)

### Properties

- [agr\_id](executor_events.workerstarted.md#agr_id)

### Methods

- [extract\_exc\_info](executor_events.workerstarted.md#extract_exc_info)

## Constructors

### constructor

• **new WorkerStarted**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

AgreementEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:220](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L220)

## Properties

### agr\_id

• `Optional` **agr\_id**: `string`

#### Inherited from

AgreementEvent.agr\_id

#### Defined in

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

Extract exception information from this event.

#### Returns

[`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

#### Inherited from

AgreementEvent.extract\_exc\_info

#### Defined in

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)
