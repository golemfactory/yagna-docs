[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentFailed

# Class: PaymentFailed

[executor/events](../modules/executor_events.md).PaymentFailed

## Hierarchy

- `AgreementEvent`

  ↳ **PaymentFailed**

## Table of contents

### Constructors

- [constructor](executor_events.paymentfailed.md#constructor)

### Properties

- [agr\_id](executor_events.paymentfailed.md#agr_id)
- [reason](executor_events.paymentfailed.md#reason)

### Methods

- [extract\_exc\_info](executor_events.paymentfailed.md#extract_exc_info)

## Constructors

### constructor

• **new PaymentFailed**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

AgreementEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:184](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L184)

## Properties

### agr\_id

• `Optional` **agr\_id**: `string`

#### Inherited from

AgreementEvent.agr\_id

#### Defined in

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

___

### reason

• **reason**: `string`

#### Defined in

[yajsapi/executor/events.ts:184](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L184)

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
