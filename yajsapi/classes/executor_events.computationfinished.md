[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ComputationFinished

# Class: ComputationFinished

[executor/events](../modules/executor_events.md).ComputationFinished

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **ComputationFinished**

## Table of contents

### Constructors

- [constructor](executor_events.computationfinished.md#constructor)

### Methods

- [extract\_exc\_info](executor_events.computationfinished.md#extract_exc_info)

## Constructors

### constructor

\+ **new ComputationFinished**(): [*ComputationFinished*](executor_events.computationfinished.md)

**Returns:** [*ComputationFinished*](executor_events.computationfinished.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L9)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
