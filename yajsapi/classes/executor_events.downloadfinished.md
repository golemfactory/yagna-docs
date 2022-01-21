# Class: DownloadFinished

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / DownloadFinished

## Class: DownloadFinished

[executor/events](../modules/executor_events.md).DownloadFinished

### Hierarchy

* [YaEvent](executor_events.yaevent.md)

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

• **new DownloadFinished**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:493](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L493)

### Properties

#### path

• `Optional` **path**: `string`

**Defined in**

[yajsapi/executor/events.ts:493](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L493)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns**

\[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

**Inherited from**

[YaEvent](executor_events.yaevent.md).[extract\_exc\_info](executor_events.yaevent.md#extract_exc_info)

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

