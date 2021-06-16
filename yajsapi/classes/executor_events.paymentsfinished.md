[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / PaymentsFinished

# Class: PaymentsFinished

[executor/events](../modules/executor_events.md).PaymentsFinished

## Hierarchy

- [YaEvent](executor_events.yaevent.md)

  ↳ **PaymentsFinished**

## Table of contents

### Constructors

- [constructor](executor_events.paymentsfinished.md#constructor)

### Methods

- [extract\_exc\_info](executor_events.paymentsfinished.md#extract_exc_info)

## Constructors

### constructor

• **new PaymentsFinished**()

#### Inherited from

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

#### Defined in

[yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L9)

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
