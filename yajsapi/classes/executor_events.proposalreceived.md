# Class: ProposalReceived

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ProposalReceived

## Class: ProposalReceived

[executor/events](../modules/executor_events.md).ProposalReceived

### Hierarchy

* [ProposalEvent](executor_events.proposalevent.md)

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

• **new ProposalReceived**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

[ProposalEvent](executor_events.proposalevent.md).[constructor](executor_events.proposalevent.md#constructor)

**Defined in**

[yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L71)

### Properties

#### prop\_id

• `Optional` **prop\_id**: `string`

**Inherited from**

[ProposalEvent](executor_events.proposalevent.md).[prop\_id](executor_events.proposalevent.md#prop_id)

**Defined in**

[yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L67)

#### provider\_id

• `Optional` **provider\_id**: `string`

**Defined in**

[yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L71)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns**

\[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

**Inherited from**

[ProposalEvent](executor_events.proposalevent.md).[extract\_exc\_info](executor_events.proposalevent.md#extract_exc_info)

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

