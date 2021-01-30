# rest/market/market

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/market](../yajsapi-2/rest_market.md) / Market

## Class: Market

[rest/market](../yajsapi-2/rest_market.md).Market

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

+ **new Market**\(`cfg`: _Configuration_\): [_Market_](rest_market.market.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cfg` | _Configuration_ |

**Returns:** [_Market_](rest_market.market.md)

Defined in: [yajsapi/rest/market.ts:264](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L264)

### Properties

#### \_api

• `Private` **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/market.ts:264](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L264)

### Methods

#### subscribe

▸ **subscribe**\(`props`: {}, `constraints`: _string_\): _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `props` | {} |
| `constraints` | _string_ |

**Returns:** _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

Defined in: [yajsapi/rest/market.ts:269](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L269)

#### subscriptions

▸ **subscriptions**\(\): _AsyncGenerator_&lt;[_Subscription_](rest_market.subscription.md), _any_, _unknown_&gt;

**Returns:** _AsyncGenerator_&lt;[_Subscription_](rest_market.subscription.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/market.ts:287](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L287)

