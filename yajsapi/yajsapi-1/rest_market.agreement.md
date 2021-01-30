# rest/market/agreement

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/market](../yajsapi-2/rest_market.md) / Agreement

## Class: Agreement

[rest/market](../yajsapi-2/rest_market.md).Agreement

### Hierarchy

* **Agreement**

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

+ **new Agreement**\(`api`: _RequestorApi_, `subscription`: [_Subscription_](rest_market.subscription.md), `agreement_id`: _string_\): [_Agreement_](rest_market.agreement.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `api` | _RequestorApi_ |
| `subscription` | [_Subscription_](rest_market.subscription.md) |
| `agreement_id` | _string_ |

**Returns:** [_Agreement_](rest_market.agreement.md)

Defined in: [yajsapi/rest/market.ts:46](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L46)

### Properties

#### \_api

• `Private` **\_api**: _any_

Defined in: [yajsapi/rest/market.ts:44](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L44)

#### \_id

• `Private` **\_id**: _any_

Defined in: [yajsapi/rest/market.ts:46](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L46)

#### \_subscription

• `Private` **\_subscription**: _any_

Defined in: [yajsapi/rest/market.ts:45](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L45)

### Methods

#### confirm

▸ **confirm**\(\): _Promise_&lt;_boolean_&gt;

**Returns:** _Promise_&lt;_boolean_&gt;

Defined in: [yajsapi/rest/market.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L67)

#### details

▸ **details**\(\): _Promise_&lt;_AgreementDetails_&gt;

**Returns:** _Promise_&lt;_AgreementDetails_&gt;

Defined in: [yajsapi/rest/market.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L62)

#### id

▸ **id**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/market.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L58)

#### terminate

▸ **terminate**\(`reason?`: _string_\): _Promise_&lt;_boolean_&gt;

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `reason` | _string_ | "Finished" |

**Returns:** _Promise_&lt;_boolean_&gt;

Defined in: [yajsapi/rest/market.ts:78](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L78)

