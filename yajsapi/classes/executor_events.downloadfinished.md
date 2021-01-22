[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / DownloadFinished

# Class: DownloadFinished

[executor/events](../modules/executor_events.md).DownloadFinished

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **DownloadFinished**

## Table of contents

### Constructors

- [constructor](executor_events.downloadfinished.md#constructor)

### Properties

- [path](executor_events.downloadfinished.md#path)

### Methods

- [extract\_exc\_info](executor_events.downloadfinished.md#extract_exc_info)

## Constructors

### constructor

\+ **new DownloadFinished**(`__namedParameters`: *Object*): [*DownloadFinished*](executor_events.downloadfinished.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*DownloadFinished*](executor_events.downloadfinished.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:467](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L467)

## Properties

### path

• `Optional` **path**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:467](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L467)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
