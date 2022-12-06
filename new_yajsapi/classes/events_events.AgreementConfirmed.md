# Class: AgreementConfirmed

[events/events](../modules/events_events.md).AgreementConfirmed

## Hierarchy

- [`BaseEvent`](events_events.BaseEvent.md)<{ `id`: `string` ; `providerId`: `string`  }\>

  ↳ **`AgreementConfirmed`**

## Table of contents

### Constructors

- [constructor](events_events.AgreementConfirmed.md#constructor)

### Properties

- [detail](events_events.AgreementConfirmed.md#detail)

## Constructors

### constructor

• **new AgreementConfirmed**(`data?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `data?` | `Object` |
| `data.id` | `string` |
| `data.providerId` | `string` |

#### Inherited from

[BaseEvent](events_events.BaseEvent.md).[constructor](events_events.BaseEvent.md#constructor)

#### Defined in

[yajsapi/events/events.ts:16](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/events/events.ts#L16)

## Properties

### detail

• `Readonly` **detail**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `id` | `string` |
| `providerId` | `string` |

#### Inherited from

[BaseEvent](events_events.BaseEvent.md).[detail](events_events.BaseEvent.md#detail)

#### Defined in

[yajsapi/events/events.ts:8](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/events/events.ts#L8)