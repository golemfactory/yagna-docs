# Class: DownloadStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / DownloadStarted

## Class: DownloadStarted

[executor/events](../modules/executor_events.md).DownloadStarted

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **DownloadStarted**

### Table of contents

#### Constructors

* [constructor](executor_events.downloadstarted.md#constructor)

#### Properties

* [path](executor_events.downloadstarted.md#path)

#### Methods

* [extract\_exc\_info](executor_events.downloadstarted.md#extract_exc_info)

### Constructors

#### constructor

* **new DownloadStarted**\(`__namedParameters`: _Object_\): [_DownloadStarted_](executor_events.downloadstarted.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_DownloadStarted_](executor_events.downloadstarted.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:478](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L478)

### Properties

#### path

• `Optional` **path**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:478](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L478)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

