# Class: SubscriptionCreated

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / SubscriptionCreated

## Class: SubscriptionCreated

[executor/events](../modules/executor_events.md).SubscriptionCreated

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **SubscriptionCreated**

### Table of contents

#### Constructors

* [constructor](executor_events.subscriptioncreated.md#constructor)

#### Properties

* [sub\_id](executor_events.subscriptioncreated.md#sub_id)

#### Methods

* [extract\_exc\_info](executor_events.subscriptioncreated.md#extract_exc_info)

### Constructors

#### constructor

* **new SubscriptionCreated**\(`__namedParameters`: _Object_\): [_SubscriptionCreated_](executor_events.subscriptioncreated.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_SubscriptionCreated_](executor_events.subscriptioncreated.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:40](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L40)

### Properties

#### sub\_id

• `Optional` **sub\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:40](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L40)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

