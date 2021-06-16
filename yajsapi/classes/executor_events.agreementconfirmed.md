# Class: AgreementConfirmed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / AgreementConfirmed

## Class: AgreementConfirmed

[executor/events](../modules/executor_events.md).AgreementConfirmed

### Hierarchy

* `AgreementEvent`

  ↳ **AgreementConfirmed**

### Table of contents

#### Constructors

* [constructor](executor_events.agreementconfirmed.md#constructor)

#### Properties

* [agr\_id](executor_events.agreementconfirmed.md#agr_id)

#### Methods

* [extract\_exc\_info](executor_events.agreementconfirmed.md#extract_exc_info)

### Constructors

#### constructor

• **new AgreementConfirmed**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

AgreementEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:137](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L137)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

AgreementEvent.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

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

