# Class: AgreementTerminated

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / AgreementTerminated

## Class: AgreementTerminated

[executor/events](../modules/executor_events.md).AgreementTerminated

### Hierarchy

* `AgreementEvent`

  ↳ **AgreementTerminated**

### Table of contents

#### Constructors

* [constructor](executor_events.agreementterminated.md#constructor)

#### Properties

* [agr\_id](executor_events.agreementterminated.md#agr_id)
* [reason](executor_events.agreementterminated.md#reason)

#### Methods

* [extract\_exc\_info](executor_events.agreementterminated.md#extract_exc_info)

### Constructors

#### constructor

• **new AgreementTerminated**\(`__namedParameters`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Overrides**

AgreementEvent.constructor

**Defined in**

[yajsapi/executor/events.ts:152](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L152)

### Properties

#### agr\_id

• `Optional` **agr\_id**: `string`

**Inherited from**

AgreementEvent.agr\_id

**Defined in**

[yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L123)

#### reason

• `Optional` **reason**: `null` \| `string`

**Defined in**

[yajsapi/executor/events.ts:152](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L152)

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

