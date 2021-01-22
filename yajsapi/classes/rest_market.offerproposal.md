[yajsapi](../README.md) / [Exports](../modules.md) / [rest/market](../modules/rest_market.md) / OfferProposal

# Class: OfferProposal

[rest/market](../modules/rest_market.md).OfferProposal

## Hierarchy

* **OfferProposal**

## Table of contents

### Constructors

- [constructor](rest_market.offerproposal.md#constructor)

### Properties

- [\_proposal](rest_market.offerproposal.md#_proposal)
- [\_subscription](rest_market.offerproposal.md#_subscription)

### Methods

- [create\_agreement](rest_market.offerproposal.md#create_agreement)
- [id](rest_market.offerproposal.md#id)
- [is\_draft](rest_market.offerproposal.md#is_draft)
- [issuer](rest_market.offerproposal.md#issuer)
- [props](rest_market.offerproposal.md#props)
- [reject](rest_market.offerproposal.md#reject)
- [respond](rest_market.offerproposal.md#respond)
- [state](rest_market.offerproposal.md#state)

## Constructors

### constructor

\+ **new OfferProposal**(`subscription`: [*Subscription*](rest_market.subscription.md), `proposal`: ProposalEvent): [*OfferProposal*](rest_market.offerproposal.md)

#### Parameters:

Name | Type |
------ | ------ |
`subscription` | [*Subscription*](rest_market.subscription.md) |
`proposal` | ProposalEvent |

**Returns:** [*OfferProposal*](rest_market.offerproposal.md)

Defined in: [yajsapi/rest/market.ts:118](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L118)

## Properties

### \_proposal

• `Private` **\_proposal**: ProposalEvent

Defined in: [yajsapi/rest/market.ts:117](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L117)

___

### \_subscription

• `Private` **\_subscription**: [*Subscription*](rest_market.subscription.md)

Defined in: [yajsapi/rest/market.ts:118](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L118)

## Methods

### create\_agreement

▸ **create_agreement**(`timeout?`: *number*): *Promise*<[*Agreement*](rest_market.agreement.md)\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`timeout` | *number* | 3600 |

**Returns:** *Promise*<[*Agreement*](rest_market.agreement.md)\>

Defined in: [yajsapi/rest/market.ts:169](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L169)

___

### id

▸ **id**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/market.ts:129](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L129)

___

### is\_draft

▸ **is_draft**(): *boolean*

**Returns:** *boolean*

Defined in: [yajsapi/rest/market.ts:141](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L141)

___

### issuer

▸ **issuer**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/market.ts:125](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L125)

___

### props

▸ **props**(): *object*

**Returns:** *object*

Defined in: [yajsapi/rest/market.ts:133](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L133)

___

### reject

▸ **reject**(`_reason?`: *null* \| *string*): *Promise*<*void*\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`_reason` | *null* \| *string* | null |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/market.ts:147](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L147)

___

### respond

▸ **respond**(`props`: *object*, `constraints`: *string*): *Promise*<*string*\>

#### Parameters:

Name | Type |
------ | ------ |
`props` | *object* |
`constraints` | *string* |

**Returns:** *Promise*<*string*\>

Defined in: [yajsapi/rest/market.ts:154](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L154)

___

### state

▸ **state**(): ProposalAllOfStateEnum

**Returns:** ProposalAllOfStateEnum

Defined in: [yajsapi/rest/market.ts:137](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L137)
