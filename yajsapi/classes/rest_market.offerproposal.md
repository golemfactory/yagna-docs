# Class: OfferProposal

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / OfferProposal

## Class: OfferProposal

[rest/market](../modules/rest_market.md).OfferProposal

### Table of contents

#### Constructors

* [constructor](rest_market.offerproposal.md#constructor)

#### Properties

* [\_proposal](rest_market.offerproposal.md#_proposal)
* [\_subscription](rest_market.offerproposal.md#_subscription)

#### Methods

* [create\_agreement](rest_market.offerproposal.md#create_agreement)
* [id](rest_market.offerproposal.md#id)
* [is\_draft](rest_market.offerproposal.md#is_draft)
* [issuer](rest_market.offerproposal.md#issuer)
* [props](rest_market.offerproposal.md#props)
* [reject](rest_market.offerproposal.md#reject)
* [respond](rest_market.offerproposal.md#respond)
* [state](rest_market.offerproposal.md#state)

### Constructors

#### constructor

• **new OfferProposal**\(`subscription`, `proposal`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `subscription` | [Subscription](rest_market.subscription.md) |
| `proposal` | `ProposalEvent` |

**Defined in**

[yajsapi/rest/market.ts:124](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L124)

### Properties

#### \_proposal

• `Private` **\_proposal**: `ProposalEvent`

**Defined in**

[yajsapi/rest/market.ts:123](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L123)

#### \_subscription

• `Private` **\_subscription**: [Subscription](rest_market.subscription.md)

**Defined in**

[yajsapi/rest/market.ts:124](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L124)

### Methods

#### create\_agreement

▸ **create\_agreement**\(`timeout?`\): `Promise`&lt;[Agreement](rest_market.agreement.md)&gt;

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `timeout` | `number` | 3600 |

**Returns**

`Promise`&lt;[Agreement](rest_market.agreement.md)&gt;

**Defined in**

[yajsapi/rest/market.ts:183](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L183)

#### id

▸ **id**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/rest/market.ts:135](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L135)

#### is\_draft

▸ **is\_draft**\(\): `boolean`

**Returns**

`boolean`

**Defined in**

[yajsapi/rest/market.ts:147](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L147)

#### issuer

▸ **issuer**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/rest/market.ts:131](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L131)

#### props

▸ **props**\(\): `object`

**Returns**

`object`

**Defined in**

[yajsapi/rest/market.ts:139](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L139)

#### reject

▸ **reject**\(`_reason?`\): `Promise`

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `_reason` | `null` \| `string` | null |

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:153](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L153)

#### respond

▸ **respond**\(`props`, `constraints`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `props` | `object` |
| `constraints` | `string` |

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:167](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L167)

#### state

▸ **state**\(\): `ProposalAllOfStateEnum`

**Returns**

`ProposalAllOfStateEnum`

**Defined in**

[yajsapi/rest/market.ts:143](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L143)

