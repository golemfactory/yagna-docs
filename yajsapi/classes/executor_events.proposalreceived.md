# Class: ProposalReceived

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ProposalReceived

## Class: ProposalReceived

[executor/events](../modules/executor_events.md).ProposalReceived

### Hierarchy

* _ProposalEvent_

  ↳ **ProposalReceived**

### Table of contents

#### Constructors

* [constructor](executor_events.proposalreceived.md#constructor)

#### Properties

* [prop\_id](executor_events.proposalreceived.md#prop_id)
* [provider\_id](executor_events.proposalreceived.md#provider_id)

#### Methods

* [extract\_exc\_info](executor_events.proposalreceived.md#extract_exc_info)

### Constructors

#### constructor

+ **new ProposalReceived**\(`__namedParameters`: _Object_\): [_ProposalReceived_](executor_events.proposalreceived.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ProposalReceived_](executor_events.proposalreceived.md)

Defined in: [yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L71)

### Properties

#### prop\_id

• `Optional` **prop\_id**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L67)

#### provider\_id

• `Optional` **provider\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L71)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

