# Class: AgreementCreated

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / AgreementCreated

## Class: AgreementCreated

[executor/events](../modules/executor_events.md).AgreementCreated

### Hierarchy

* `AgreementEvent`

  ↳ **AgreementCreated**

### Table of contents

#### Constructors

* [constructor](executor_events.agreementcreated.md#constructor)

#### Properties

* [agr\_id](executor_events.agreementcreated.md#agr_id)
* [provider\_id](executor_events.agreementcreated.md#provider_id)
* [provider\_info](executor_events.agreementcreated.md#provider_info)

#### Methods

* [extract\_exc\_info](executor_events.agreementcreated.md#extract_exc_info)

### Constructors

#### constructor

• **new AgreementCreated**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

AgreementEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:128](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L128)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

AgreementEvent.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### provider\_id

• `Optional` **provider\_id**: `string`

**Defined in**

[yajsapi/executor/events.ts:127](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L127)

#### provider\_info

• `Optional` **provider\_info**: [NodeInfo](props.nodeinfo.md)

**Defined in**

[yajsapi/executor/events.ts:128](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L128)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns**

\[`undefined` \| `null` \| `Error`, [YaEvent](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

**Inherited from**

AgreementEvent.extract\_exc\_info

**Defined in**

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)

