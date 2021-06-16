# Class: Market

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / Market

## Class: Market

[rest/market](../modules/rest_market.md).Market

### Table of contents

#### Constructors

* [constructor](rest_market.market.md#constructor)

#### Properties

* [\_api](rest_market.market.md#_api)

#### Methods

* [subscribe](rest_market.market.md#subscribe)
* [subscriptions](rest_market.market.md#subscriptions)

### Constructors

#### constructor

• **new Market**\(`cfg`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `cfg` | `Configuration` |

**Defined in**

[yajsapi/rest/market.ts:286](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L286)

### Properties

#### \_api

• `Private` **\_api**: `RequestorApi`

**Defined in**

[yajsapi/rest/market.ts:286](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L286)

### Methods

#### subscribe

▸ **subscribe**\(`props`, `constraints`\): `Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `props` | `Object` |
| `constraints` | `string` |

**Returns**

`Promise`&lt;[Subscription](rest_market.subscription.md)&gt;

**Defined in**

[yajsapi/rest/market.ts:291](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L291)

#### subscriptions

▸ **subscriptions**\(\): `AsyncGenerator`&lt;[Subscription](rest_market.subscription.md), any, unknown&gt;

**Returns**

`AsyncGenerator`&lt;[Subscription](rest_market.subscription.md), any, unknown&gt;

**Defined in**

[yajsapi/rest/market.ts:309](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L309)

