[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / WorkerFinished

# Class: WorkerFinished

[executor/events](../modules/executor_events.md).WorkerFinished

## Hierarchy

* *AgreementEvent*

  ↳ **WorkerFinished**

## Table of contents

### Constructors

- [constructor](executor_events.workerfinished.md#constructor)

### Properties

- [agr\_id](executor_events.workerfinished.md#agr_id)
- [exception](executor_events.workerfinished.md#exception)

### Methods

- [extract\_exc\_info](executor_events.workerfinished.md#extract_exc_info)

## Constructors

### constructor

\+ **new WorkerFinished**(`__namedParameters`: *Object*): [*WorkerFinished*](executor_events.workerfinished.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*WorkerFinished*](executor_events.workerfinished.md)

Defined in: [yajsapi/executor/events.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L247)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### exception

• `Optional` **exception**: *undefined* \| *null* \| Error= null

Defined in: [yajsapi/executor/events.ts:247](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L247)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Defined in: [yajsapi/executor/events.ts:255](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L255)
