# Class: DownloadFinished

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / DownloadFinished

## Class: DownloadFinished

[executor/events](../modules/executor_events.md).DownloadFinished

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **DownloadFinished**

### Table of contents

#### Constructors

* [constructor](executor_events.downloadfinished.md#constructor)

#### Properties

* [path](executor_events.downloadfinished.md#path)

#### Methods

* [extract\_exc\_info](executor_events.downloadfinished.md#extract_exc_info)

### Constructors

#### constructor

+ **new DownloadFinished**\(`__namedParameters`: _Object_\): [_DownloadFinished_](executor_events.downloadfinished.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_DownloadFinished_](executor_events.downloadfinished.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:487](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L487)

### Properties

#### path

• `Optional` **path**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:487](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L487)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

