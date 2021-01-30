# executor/events/noproposalsconfirmed

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / NoProposalsConfirmed

## Class: NoProposalsConfirmed

[executor/events](../yajsapi-2/executor_events.md).NoProposalsConfirmed

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **NoProposalsConfirmed**

### Table of contents

#### Constructors

* [constructor](executor_events.noproposalsconfirmed.md#constructor)

#### Properties

* [num\_offers](executor_events.noproposalsconfirmed.md#num_offers)
* [timeout](executor_events.noproposalsconfirmed.md#timeout)

#### Methods

* [extract\_exc\_info](executor_events.noproposalsconfirmed.md#extract_exc_info)

### Constructors

#### constructor

+ **new NoProposalsConfirmed**\(`__namedParameters`: _Object_\): [_NoProposalsConfirmed_](executor_events.noproposalsconfirmed.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_NoProposalsConfirmed_](executor_events.noproposalsconfirmed.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:113](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L113)

### Properties

#### num\_offers

• `Optional` **num\_offers**: _undefined_ \| _number_

Defined in: [yajsapi/executor/events.ts:112](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L112)

#### timeout

• `Optional` **timeout**: _undefined_ \| _number_

Defined in: [yajsapi/executor/events.ts:113](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L113)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)

