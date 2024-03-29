# Class: CollectFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CollectFailed

## Class: CollectFailed

[executor/events](../modules/executor_events.md).CollectFailed

### Hierarchy

* [YaEvent](executor_events.yaevent.md)

  ↳ **CollectFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.collectfailed.md#constructor)

#### Properties

* [reason](executor_events.collectfailed.md#reason)
* [sub\_id](executor_events.collectfailed.md#sub_id)

#### Methods

* [extract\_exc\_info](executor_events.collectfailed.md#extract_exc_info)

### Constructors

#### constructor

• **new CollectFailed**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L57)

### Properties

#### reason

• **reason**: `string`

**Defined in**

[yajsapi/executor/events.ts:57](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L57)

#### sub\_id

• **sub\_id**: `string`

**Defined in**

[yajsapi/executor/events.ts:56](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L56)

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

