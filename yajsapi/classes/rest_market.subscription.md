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

Defined in: [yajsapi/rest/market.ts:188](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L188)

## Properties

### \_api

• **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/market.ts:184](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L184)

___

### \_deleted

• `Private` **\_deleted**: *boolean*

Defined in: [yajsapi/rest/market.ts:187](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L187)

___

### \_details

• `Private` **\_details**: *any*

Defined in: [yajsapi/rest/market.ts:188](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L188)

___

### \_id

• `Private` **\_id**: *string*

Defined in: [yajsapi/rest/market.ts:185](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L185)

___

### \_open

• `Private` **\_open**: *boolean*

Defined in: [yajsapi/rest/market.ts:186](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L186)

## Methods

### close

▸ **close**(): *void*

**Returns:** *void*

Defined in: [yajsapi/rest/market.ts:206](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L206)

___

### delete

▸ **delete**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/market.ts:223](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L223)

___

### details

▸ **details**(): Demand

**Returns:** Demand

Defined in: [yajsapi/rest/market.ts:218](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L218)

___

### done

▸ **done**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/rest/market.ts:214](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L214)

___

### events

▸ **events**(`cancellationToken?`: *any*): *AsyncGenerator*<[*OfferProposal*](rest_market.offerproposal.md), *any*, *unknown*\>

#### Parameters:

Name | Type |
------ | ------ |
`cancellationToken?` | *any* |

**Returns:** *AsyncGenerator*<[*OfferProposal*](rest_market.offerproposal.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/market.ts:230](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L230)

___

### id

▸ **id**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/market.ts:202](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L202)

___

### ready

▸ **ready**(): *Promise*<[*Subscription*](rest_market.subscription.md)\>

**Returns:** *Promise*<[*Subscription*](rest_market.subscription.md)\>

Defined in: [yajsapi/rest/market.ts:210](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L210)
