[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / NoProposalsConfirmed

# Class: NoProposalsConfirmed

[executor/events](../modules/executor_events.md).NoProposalsConfirmed

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **NoProposalsConfirmed**

## Table of contents

### Constructors

- [constructor](executor_events.noproposalsconfirmed.md#constructor)

### Properties

- [num\_offers](executor_events.noproposalsconfirmed.md#num_offers)
- [timeout](executor_events.noproposalsconfirmed.md#timeout)

### Methods

- [extract\_exc\_info](executor_events.noproposalsconfirmed.md#extract_exc_info)

## Constructors

### constructor

\+ **new NoProposalsConfirmed**(`__namedParameters`: *Object*): [*NoProposalsConfirmed*](executor_events.noproposalsconfirmed.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*NoProposalsConfirmed*](executor_events.noproposalsconfirmed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:113](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L113)

## Properties

### num\_offers

• `Optional` **num\_offers**: *undefined* \| *number*

Defined in: [yajsapi/executor/events.ts:112](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L112)

___

### timeout

• `Optional` **timeout**: *undefined* \| *number*

Defined in: [yajsapi/executor/events.ts:113](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L113)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
