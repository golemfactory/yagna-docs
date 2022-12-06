# Class: ActivityCreated

[events/events](../modules/events_events.md).ActivityCreated

## Hierarchy

- [`BaseEvent`](events_events.BaseEvent.md)<{ `id`: `string` ; `agreementId`: `string`  }\>

  ↳ **`ActivityCreated`**

## Table of contents

### Constructors

- [constructor](events_events.ActivityCreated.md#constructor)

### Properties

- [detail](events_events.ActivityCreated.md#detail)

## Constructors

### constructor

• **new ActivityCreated**(`data?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `data?` | `Object` |
| `data.id` | `string` |
| `data.agreementId` | `string` |

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
| `agreementId` | `string` |

#### Inherited from

[BaseEvent](events_events.BaseEvent.md).[detail](events_events.BaseEvent.md#detail)

#### Defined in

[yajsapi/events/events.ts:8](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/events/events.ts#L8)