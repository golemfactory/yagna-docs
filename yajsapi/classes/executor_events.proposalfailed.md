# Class: ProposalFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ProposalFailed

## Class: ProposalFailed

[executor/events](../modules/executor_events.md).ProposalFailed

### Hierarchy

* _ProposalEvent_

  ↳ **ProposalFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.proposalfailed.md#constructor)

#### Properties

* [prop\_id](executor_events.proposalfailed.md#prop_id)
* [reason](executor_events.proposalfailed.md#reason)

#### Methods

* [extract\_exc\_info](executor_events.proposalfailed.md#extract_exc_info)

### Constructors

#### constructor

* **new ProposalFailed**\(`__namedParameters`: _Object_\): [_ProposalFailed_](executor_events.proposalfailed.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ProposalFailed_](executor_events.proposalfailed.md)

Defined in: [yajsapi/executor/events.ts:103](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L103)

### Properties

#### prop\_id

• `Optional` **prop\_id**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L67)

#### reason

• `Optional` **reason**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:103](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L103)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

