[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / InvoiceReceived

# Class: InvoiceReceived

[executor/events](../modules/executor_events.md).InvoiceReceived

## Hierarchy

- `AgreementEvent`

  ↳ **InvoiceReceived**

## Table of contents

### Constructors

- [constructor](executor_events.invoicereceived.md#constructor)

### Properties

- [agr\_id](executor_events.invoicereceived.md#agr_id)
- [amount](executor_events.invoicereceived.md#amount)
- [inv\_id](executor_events.invoicereceived.md#inv_id)

### Methods

- [extract\_exc\_info](executor_events.invoicereceived.md#extract_exc_info)

## Constructors

### constructor

• **new InvoiceReceived**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

AgreementEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:211](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L211)

## Properties

### agr\_id

• `Optional` **agr\_id**: `string`

#### Inherited from

AgreementEvent.agr\_id

#### Defined in

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

___

### amount

• `Optional` **amount**: `string`

#### Defined in

[yajsapi/executor/events.ts:211](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L211)

___

### inv\_id

• `Optional` **inv\_id**: `string`

#### Defined in

[yajsapi/executor/events.ts:210](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L210)

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
