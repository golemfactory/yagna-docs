[yajsapi](../README.md) / [Exports](../modules.md) / [rest/market](../modules/rest_market.md) / Subscription

# Class: Subscription

[rest/market](../modules/rest_market.md).Subscription

## Hierarchy

* **Subscription**

## Table of contents

### Constructors

- [constructor](rest_market.subscription.md#constructor)

### Properties

- [\_api](rest_market.subscription.md#_api)
- [\_deleted](rest_market.subscription.md#_deleted)
- [\_details](rest_market.subscription.md#_details)
- [\_id](rest_market.subscription.md#_id)
- [\_open](rest_market.subscription.md#_open)

### Methods

- [close](rest_market.subscription.md#close)
- [delete](rest_market.subscription.md#delete)
- [details](rest_market.subscription.md#details)
- [done](rest_market.subscription.md#done)
- [events](rest_market.subscription.md#events)
- [id](rest_market.subscription.md#id)
- [ready](rest_market.subscription.md#ready)

## Constructors

### constructor

\+ **new Subscription**(`api`: *RequestorApi*, `subscription_id`: *string*, `_details?`: *null* \| Demand): [*Subscription*](rest_market.subscription.md)

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`api` | *RequestorApi* | - |
`subscription_id` | *string* | - |
`_details` | *null* \| Demand | null |

**Returns:** [*Subscription*](rest_market.subscription.md)

Defined in: [yajsapi/rest/market.ts:187](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L187)

## Properties

### \_api

• **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/market.ts:183](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L183)

___

### \_deleted

• `Private` **\_deleted**: *boolean*

Defined in: [yajsapi/rest/market.ts:186](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L186)

___

### \_details

• `Private` **\_details**: *any*

Defined in: [yajsapi/rest/market.ts:187](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L187)

___

### \_id

• `Private` **\_id**: *string*

Defined in: [yajsapi/rest/market.ts:184](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L184)

___

### \_open

• `Private` **\_open**: *boolean*

Defined in: [yajsapi/rest/market.ts:185](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L185)

## Methods

### close

▸ **close**(): *void*

**Returns:** *void*

Defined in: [yajsapi/rest/market.ts:205](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L205)

___

### delete

▸ **delete**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/market.ts:222](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L222)

___

### details

▸ **details**(): Demand

**Returns:** Demand

Defined in: [yajsapi/rest/market.ts:217](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L217)

___

### done

▸ **done**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/market.ts:213](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L213)

___

### events

▸ **events**(`cancellationToken?`: *any*): *AsyncGenerator*<[*OfferProposal*](rest_market.offerproposal.md), *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`cancellationToken?` | *any* |

**Returns:** *AsyncGenerator*<[*OfferProposal*](rest_market.offerproposal.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/market.ts:229](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L229)

___

### id

▸ **id**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/market.ts:201](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L201)

___

### ready

▸ **ready**(): *Promise*<[*Subscription*](rest_market.subscription.md)\>

**Returns:** *Promise*<[*Subscription*](rest_market.subscription.md)\>

Defined in: [yajsapi/rest/market.ts:209](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L209)
