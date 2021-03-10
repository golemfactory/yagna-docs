# Class: ProposalResponded

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ProposalResponded

## Class: ProposalResponded

[executor/events](../modules/executor_events.md).ProposalResponded

### Hierarchy

* _ProposalEvent_

  ↳ **ProposalResponded**

### Table of contents

#### Constructors

* [constructor](executor_events.proposalresponded.md#constructor)

#### Properties

* [prop\_id](executor_events.proposalresponded.md#prop_id)

#### Methods

* [extract\_exc\_info](executor_events.proposalresponded.md#extract_exc_info)

### Constructors

#### constructor

* **new ProposalResponded**\(`__namedParameters`: _Object_\): [_ProposalResponded_](executor_events.proposalresponded.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ProposalResponded_](executor_events.proposalresponded.md)

Defined in: [yajsapi/executor/events.ts:88](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L88)

### Properties

#### prop\_id

• `Optional` **prop\_id**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L67)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

