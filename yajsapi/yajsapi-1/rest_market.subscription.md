# rest/market/subscription

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/market](../yajsapi-2/rest_market.md) / Subscription

## Class: Subscription

[rest/market](../yajsapi-2/rest_market.md).Subscription

### Hierarchy

* **Subscription**

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

+ **new Subscription**\(`api`: _RequestorApi_, `subscription_id`: _string_, `_details?`: _null_ \| Demand\): [_Subscription_](rest_market.subscription.md)

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `api` | _RequestorApi_ | - |
| `subscription_id` | _string_ | - |
| `_details` | _null_ \| Demand | null |

**Returns:** [_Subscription_](rest_market.subscription.md)

Defined in: [yajsapi/rest/market.ts:187](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L187)

### Properties

#### \_api

• **\_api**: _RequestorApi_

Defined in: [yajsapi/rest/market.ts:183](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L183)

#### \_deleted

• `Private` **\_deleted**: _boolean_

Defined in: [yajsapi/rest/market.ts:186](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L186)

#### \_details

• `Private` **\_details**: _any_

Defined in: [yajsapi/rest/market.ts:187](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L187)

#### \_id

• `Private` **\_id**: _string_

Defined in: [yajsapi/rest/market.ts:184](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L184)

#### \_open

• `Private` **\_open**: _boolean_

Defined in: [yajsapi/rest/market.ts:185](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L185)

### Methods

#### close

▸ **close**\(\): _void_

**Returns:** _void_

Defined in: [yajsapi/rest/market.ts:205](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L205)

#### delete

▸ **delete**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/market.ts:222](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L222)

#### details

▸ **details**\(\): Demand

**Returns:** Demand

Defined in: [yajsapi/rest/market.ts:217](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L217)

#### done

▸ **done**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/market.ts:213](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L213)

#### events

▸ **events**\(`cancellationToken?`: _any_\): _AsyncGenerator_&lt;[_OfferProposal_](rest_market.offerproposal.md), _any_, _unknown_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cancellationToken?` | _any_ |

**Returns:** _AsyncGenerator_&lt;[_OfferProposal_](rest_market.offerproposal.md), _any_, _unknown_&gt;

Defined in: [yajsapi/rest/market.ts:229](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L229)

#### id

▸ **id**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/market.ts:201](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L201)

#### ready

▸ **ready**\(\): _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

**Returns:** _Promise_&lt;[_Subscription_](rest_market.subscription.md)&gt;

Defined in: [yajsapi/rest/market.ts:209](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L209)

