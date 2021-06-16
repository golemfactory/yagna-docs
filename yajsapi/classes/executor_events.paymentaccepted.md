[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentAccepted

# Class: PaymentAccepted

[executor/events](../modules/executor_events.md).PaymentAccepted

## Hierarchy

- `AgreementEvent`

  ↳ **PaymentAccepted**

## Table of contents

### Constructors

- [constructor](executor_events.paymentaccepted.md#constructor)

### Properties

- [agr\_id](executor_events.paymentaccepted.md#agr_id)
- [amount](executor_events.paymentaccepted.md#amount)
- [inv\_id](executor_events.paymentaccepted.md#inv_id)

### Methods

- [extract\_exc\_info](executor_events.paymentaccepted.md#extract_exc_info)

## Constructors

### constructor

• **new PaymentAccepted**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

AgreementEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:173](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L173)

## Properties

### agr\_id

• `Optional` **agr\_id**: `string`

#### Inherited from

AgreementEvent.agr\_id

#### Defined in

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

___

### amount

• **amount**: `string`

#### Defined in

[yajsapi/executor/events.ts:173](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L173)

___

### inv\_id

• **inv\_id**: `string`

#### Defined in

[yajsapi/executor/events.ts:172](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L172)

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
