[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ComputationStarted

# Class: ComputationStarted

[executor/events](../modules/executor_events.md).ComputationStarted

## Hierarchy

- [YaEvent](executor_events.yaevent.md)

  ↳ **ComputationStarted**

## Table of contents

### Constructors

- [constructor](executor_events.computationstarted.md#constructor)

### Properties

- [expires](executor_events.computationstarted.md#expires)

### Methods

- [extract\_exc\_info](executor_events.computationstarted.md#extract_exc_info)

## Constructors

### constructor

• **new ComputationStarted**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

#### Defined in

[yajsapi/executor/events.ts:23](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L23)

## Properties

### expires

• `Optional` **expires**: `number`

#### Defined in

[yajsapi/executor/events.ts:23](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L23)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

Extract exception information from this event.

#### Returns

[`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

#### Inherited from

[YaEvent](executor_events.yaevent.md).[extract_exc_info](executor_events.yaevent.md#extract_exc_info)

#### Defined in

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)
