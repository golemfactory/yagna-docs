# Class: ProposalEvent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ProposalEvent

## Class: ProposalEvent

[executor/events](../modules/executor_events.md).ProposalEvent

### Hierarchy

* [YaEvent](executor_events.yaevent.md)

  ↳ **ProposalEvent**

  ↳↳ [ProposalReceived](executor_events.proposalreceived.md)

  ↳↳ [ProposalRejected](executor_events.proposalrejected.md)

  ↳↳ [ProposalResponded](executor_events.proposalresponded.md)

  ↳↳ [ProposalConfirmed](executor_events.proposalconfirmed.md)

  ↳↳ [ProposalFailed](executor_events.proposalfailed.md)

### Table of contents

#### Constructors

* [constructor](executor_events.proposalevent.md#constructor)

#### Properties

* [prop\_id](executor_events.proposalevent.md#prop_id)

#### Methods

* [extract\_exc\_info](executor_events.proposalevent.md#extract_exc_info)

### Constructors

#### constructor

• **new ProposalEvent**\(\)

**Inherited from**

[YaEvent](executor_events.yaevent.md).[constructor](executor_events.yaevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L9)

### Properties

#### prop\_id

• `Optional` **prop\_id**: `string`

**Defined in**

[yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L67)

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

