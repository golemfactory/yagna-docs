# Class: SubscriptionFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / SubscriptionFailed

## Class: SubscriptionFailed

[executor/events](../modules/executor_events.md).SubscriptionFailed

### Hierarchy

* [YaEvent](executor_events.yaevent.md)

  ↳ **SubscriptionFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.subscriptionfailed.md#constructor)

#### Properties

* [reason](executor_events.subscriptionfailed.md#reason)

#### Methods

* [extract\_exc\_info](executor_events.subscriptionfailed.md#extract_exc_info)

### Constructors

#### constructor

• **new SubscriptionFailed**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:48](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L48)

### Properties

#### reason

• `Optional` **reason**: `string`

**Defined in**

[yajsapi/executor/events.ts:48](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L48)

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

