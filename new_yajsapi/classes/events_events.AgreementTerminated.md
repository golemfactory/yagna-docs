# Class: AgreementTerminated

[events/events](../modules/events_events.md).AgreementTerminated

## Hierarchy

- [`BaseEvent`](events_events.BaseEvent.md)<{ `id`: `string` ; `providerId`: `string` ; `reason?`: `string`  }\>

  ↳ **`AgreementTerminated`**

## Table of contents

### Constructors

- [constructor](events_events.AgreementTerminated.md#constructor)

### Properties

- [detail](events_events.AgreementTerminated.md#detail)

## Constructors

### constructor

• **new AgreementTerminated**(`data?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `data?` | `Object` |
| `data.id` | `string` |
| `data.providerId` | `string` |
| `data.reason?` | `string` |

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
| `reason?` | `string` |

#### Inherited from

[BaseEvent](events_events.BaseEvent.md).[detail](events_events.BaseEvent.md#detail)

#### Defined in

[yajsapi/events/events.ts:8](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/events/events.ts#L8)