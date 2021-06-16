# Class: Subscription

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / Subscription

## Class: Subscription

[rest/market](../modules/rest_market.md).Subscription

### Table of contents

#### Constructors

* [constructor](rest_market.subscription.md#constructor)

#### Properties

* [\_api](rest_market.subscription.md#_api)
* [\_deleted](rest_market.subscription.md#_deleted)
* [\_details](rest_market.subscription.md#_details)
* [\_id](rest_market.subscription.md#_id)
* [\_open](rest_market.subscription.md#_open)

#### Methods

* [close](rest_market.subscription.md#close)
* [delete](rest_market.subscription.md#delete)
* [details](rest_market.subscription.md#details)
* [done](rest_market.subscription.md#done)
* [events](rest_market.subscription.md#events)
* [id](rest_market.subscription.md#id)
* [ready](rest_market.subscription.md#ready)

### Constructors

#### constructor

• **new Subscription**\(`api`, `subscription_id`, `_details?`\)

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `api` | `RequestorApi` | `undefined` |
| `subscription_id` | `string` | `undefined` |
| `_details` | `null` \| `Demand` | null |

**Defined in**

[yajsapi/rest/market.ts:201](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L201)

### Properties

#### \_api

• **\_api**: `RequestorApi`

**Defined in**

[yajsapi/rest/market.ts:197](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L197)

#### \_deleted

• `Private` **\_deleted**: `boolean`

**Defined in**

[yajsapi/rest/market.ts:200](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L200)

#### \_details

• `Private` **\_details**: `any`

**Defined in**

[yajsapi/rest/market.ts:201](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L201)

#### \_id

• `Private` **\_id**: `string`

**Defined in**

[yajsapi/rest/market.ts:198](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L198)

#### \_open

• `Private` **\_open**: `boolean`

**Defined in**

[yajsapi/rest/market.ts:199](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L199)

### Methods

#### close

▸ **close**\(\): `void`

**Returns**

`void`

**Defined in**

[yajsapi/rest/market.ts:219](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L219)

#### delete

▸ **delete**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:236](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L236)

#### details

▸ **details**\(\): `Demand`

**Returns**

`Demand`

**Defined in**

[yajsapi/rest/market.ts:231](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L231)

#### done

▸ **done**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:227](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L227)

#### events

▸ **events**\(`cancellationToken?`\): `AsyncGenerator`&lt;[OfferProposal](rest_market.offerproposal.md), any, unknown&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `cancellationToken?` | `any` |

**Returns**

`AsyncGenerator`&lt;[OfferProposal](rest_market.offerproposal.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/market.ts:243](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L243)

#### id

▸ **id**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/rest/market.ts:215](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L215)

#### ready

▸ **ready**\(\): `Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Returns**

`Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Defined in**

[yajsapi/rest/market.ts:223](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L223)

