# Class: OfferProposal

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / OfferProposal

## Class: OfferProposal

[rest/market](../modules/rest_market.md).OfferProposal

### Hierarchy

* **OfferProposal**

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

* **new OfferProposal**\(`subscription`: [_Subscription_](rest_market.subscription.md), `proposal`: ProposalEvent\): [_OfferProposal_](rest_market.offerproposal.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `subscription` | [_Subscription_](rest_market.subscription.md) |
| `proposal` | ProposalEvent |

**Returns:** [_OfferProposal_](rest_market.offerproposal.md)

Defined in: [yajsapi/rest/market.ts:118](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L118)

### Properties

#### \_proposal

• `Private` **\_proposal**: ProposalEvent

Defined in: [yajsapi/rest/market.ts:117](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L117)

#### \_subscription

• `Private` **\_subscription**: [_Subscription_](rest_market.subscription.md)

Defined in: [yajsapi/rest/market.ts:118](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L118)

### Methods

#### create\_agreement

▸ **create\_agreement**\(`timeout?`: _number_\): _Promise_&lt;[_Agreement_](rest_market.agreement.md)&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `timeout` | _number_ | 3600 |

**Returns:** _Promise_&lt;[_Agreement_](rest_market.agreement.md)&gt;

Defined in: [yajsapi/rest/market.ts:170](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L170)

#### id

▸ **id**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/market.ts:129](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L129)

#### is\_draft

▸ **is\_draft**\(\): _boolean_

**Returns:** _boolean_

Defined in: [yajsapi/rest/market.ts:141](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L141)

#### issuer

▸ **issuer**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/market.ts:125](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L125)

#### props

▸ **props**\(\): _object_

**Returns:** _object_

Defined in: [yajsapi/rest/market.ts:133](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L133)

#### reject

▸ **reject**\(`_reason?`: _null_ \| _string_\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `_reason` | _null_ \| _string_ | null |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/market.ts:147](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L147)

#### respond

▸ **respond**\(`props`: _object_, `constraints`: _string_\): _Promise_&lt;_string_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | _object_ |
| `constraints` | _string_ |

**Returns:** _Promise_&lt;_string_&gt;

Defined in: [yajsapi/rest/market.ts:154](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L154)

#### state

▸ **state**\(\): ProposalAllOfStateEnum

**Returns:** ProposalAllOfStateEnum

Defined in: [yajsapi/rest/market.ts:137](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L137)

