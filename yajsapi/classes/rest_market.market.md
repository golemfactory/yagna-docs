# Class: Market

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / Market

## Class: Market

[rest/market](../modules/rest_market.md).Market

### Hierarchy

* **Market**

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

* **new Market**\(`cfg`: _Configuration_\): [_Market_](rest_market.market.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cfg` | _Configuration_ |

**Returns:** [_Market_](rest_market.market.md)

Defined in: [yajsapi/rest/market.ts:267](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L267)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/market.ts:267](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L267)

### Methods

#### subscribe

▸ **subscribe**\(`props`: {}, `constraints`: _string_\): _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | {} |
| `constraints` | _string_ |

**Returns:** _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

Defined in: [yajsapi/rest/market.ts:272](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L272)

#### subscriptions

▸ **subscriptions**\(\): _AsyncGenerator_&lt;[_Subscription_](rest_market.subscription.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Subscription_](rest_market.subscription.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/market.ts:290](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/market.ts#L290)

