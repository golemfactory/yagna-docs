[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / SubscriptionCreated

# Class: SubscriptionCreated

[executor/events](../modules/executor_events.md).SubscriptionCreated

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **SubscriptionCreated**

## Table of contents

### Constructors

- [constructor](executor_events.subscriptioncreated.md#constructor)

### Properties

- [sub\_id](executor_events.subscriptioncreated.md#sub_id)

### Methods

- [extract\_exc\_info](executor_events.subscriptioncreated.md#extract_exc_info)

## Constructors

### constructor

\+ **new SubscriptionCreated**(`__namedParameters`: *Object*): [*SubscriptionCreated*](executor_events.subscriptioncreated.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*SubscriptionCreated*](executor_events.subscriptioncreated.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L40)

## Properties

### sub\_id

• `Optional` **sub\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L40)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
