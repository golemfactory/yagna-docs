# Class: SubscriptionFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / SubscriptionFailed

## Class: SubscriptionFailed

[executor/events](../modules/executor_events.md).SubscriptionFailed

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

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

* **new SubscriptionFailed**\(`__namedParameters`: _Object_\): [_SubscriptionFailed_](executor_events.subscriptionfailed.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_SubscriptionFailed_](executor_events.subscriptionfailed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:48](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L48)

### Properties

#### reason

• `Optional` **reason**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:48](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L48)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

