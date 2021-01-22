[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / CollectFailed

# Class: CollectFailed

[executor/events](../modules/executor_events.md).CollectFailed

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **CollectFailed**

## Table of contents

### Constructors

- [constructor](executor_events.collectfailed.md#constructor)

### Properties

- [reason](executor_events.collectfailed.md#reason)
- [sub\_id](executor_events.collectfailed.md#sub_id)

### Methods

- [extract\_exc\_info](executor_events.collectfailed.md#extract_exc_info)

## Constructors

### constructor

\+ **new CollectFailed**(`__namedParameters`: *Object*): [*CollectFailed*](executor_events.collectfailed.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*CollectFailed*](executor_events.collectfailed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L57)

## Properties

### reason

• **reason**: *string*

Defined in: [yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L57)

___

### sub\_id

• **sub\_id**: *string*

Defined in: [yajsapi/executor/events.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L56)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
