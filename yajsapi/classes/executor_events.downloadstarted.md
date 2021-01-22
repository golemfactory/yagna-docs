[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / DownloadStarted

# Class: DownloadStarted

[executor/events](../modules/executor_events.md).DownloadStarted

## Hierarchy

* [*YaEvent*](executor_events.yaevent.md)

  ↳ **DownloadStarted**

## Table of contents

### Constructors

- [constructor](executor_events.downloadstarted.md#constructor)

### Properties

- [path](executor_events.downloadstarted.md#path)

### Methods

- [extract\_exc\_info](executor_events.downloadstarted.md#extract_exc_info)

## Constructors

### constructor

\+ **new DownloadStarted**(`__namedParameters`: *Object*): [*DownloadStarted*](executor_events.downloadstarted.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*DownloadStarted*](executor_events.downloadstarted.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:458](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L458)

## Properties

### path

• `Optional` **path**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:458](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L458)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
