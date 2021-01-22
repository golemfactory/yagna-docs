[yajsapi](../README.md) / [Exports](../modules.md) / [rest/market](../modules/rest_market.md) / Market

# Class: Market

[rest/market](../modules/rest_market.md).Market

## Hierarchy

* **Market**

## Table of contents

### Constructors

- [constructor](rest_market.market.md#constructor)

### Properties

- [\_api](rest_market.market.md#_api)

### Methods

- [subscribe](rest_market.market.md#subscribe)
- [subscriptions](rest_market.market.md#subscriptions)

## Constructors

### constructor

\+ **new Market**(`cfg`: *Configuration*): [*Market*](rest_market.market.md)

#### Parameters:

Name | Type |
------ | ------ |
`cfg` | *Configuration* |

**Returns:** [*Market*](rest_market.market.md)

Defined in: [yajsapi/rest/market.ts:264](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L264)

## Properties

### \_api

• `Private` **\_api**: *RequestorApi*

Defined in: [yajsapi/rest/market.ts:264](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L264)

## Methods

### subscribe

▸ **subscribe**(`props`: {}, `constraints`: *string*): *Promise*<[*Subscription*](rest_market.subscription.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`props` | {} |
`constraints` | *string* |

**Returns:** *Promise*<[*Subscription*](rest_market.subscription.md)\>

Defined in: [yajsapi/rest/market.ts:269](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L269)

___

### subscriptions

▸ **subscriptions**(): *AsyncGenerator*<[*Subscription*](rest_market.subscription.md), *any*, *unknown*\>

**Returns:** *AsyncGenerator*<[*Subscription*](rest_market.subscription.md), *any*, *unknown*\>

Defined in: [yajsapi/rest/market.ts:287](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L287)
