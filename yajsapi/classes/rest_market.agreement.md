# Class: Agreement

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/market](../modules/rest_market.md) / Agreement

## Class: Agreement

[rest/market](../modules/rest_market.md).Agreement

### Table of contents

#### Constructors

* [constructor](rest_market.agreement.md#constructor)

#### Properties

* [\_api](rest_market.agreement.md#_api)
* [\_id](rest_market.agreement.md#_id)
* [\_subscription](rest_market.agreement.md#_subscription)

#### Methods

* [confirm](rest_market.agreement.md#confirm)
* [details](rest_market.agreement.md#details)
* [id](rest_market.agreement.md#id)
* [terminate](rest_market.agreement.md#terminate)

### Constructors

#### constructor

• **new Agreement**\(`api`, `subscription`, `agreement_id`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `api` | `RequestorApi` |
| `subscription` | [Subscription](rest_market.subscription.md) |
| `agreement_id` | `string` |

**Defined in**

[yajsapi/rest/market.ts:47](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L47)

### Properties

#### \_api

• `Private` **\_api**: `any`

**Defined in**

[yajsapi/rest/market.ts:45](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L45)

#### \_id

• `Private` **\_id**: `any`

**Defined in**

[yajsapi/rest/market.ts:47](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L47)

#### \_subscription

• `Private` **\_subscription**: `any`

**Defined in**

[yajsapi/rest/market.ts:46](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L46)

### Methods

#### confirm

▸ **confirm**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:68](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L68)

#### details

▸ **details**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:63](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L63)

#### id

▸ **id**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/rest/market.ts:59](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L59)

#### terminate

▸ **terminate**\(`reason?`\): `Promise`

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `reason` | `string` | "Finished" |

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/market.ts:84](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/market.ts#L84)

