[yajsapi](../README.md) / [Exports](../modules.md) / [rest/market](../modules/rest_market.md) / Agreement

# Class: Agreement

[rest/market](../modules/rest_market.md).Agreement

## Hierarchy

* **Agreement**

## Table of contents

### Constructors

- [constructor](rest_market.agreement.md#constructor)

### Properties

- [\_api](rest_market.agreement.md#_api)
- [\_id](rest_market.agreement.md#_id)
- [\_subscription](rest_market.agreement.md#_subscription)

### Methods

- [confirm](rest_market.agreement.md#confirm)
- [details](rest_market.agreement.md#details)
- [id](rest_market.agreement.md#id)
- [terminate](rest_market.agreement.md#terminate)

## Constructors

### constructor

\+ **new Agreement**(`api`: *RequestorApi*, `subscription`: [*Subscription*](rest_market.subscription.md), `agreement_id`: *string*): [*Agreement*](rest_market.agreement.md)

#### Parameters:

Name | Type |
------ | ------ |
`api` | *RequestorApi* |
`subscription` | [*Subscription*](rest_market.subscription.md) |
`agreement_id` | *string* |

**Returns:** [*Agreement*](rest_market.agreement.md)

Defined in: [yajsapi/rest/market.ts:46](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L46)

## Properties

### \_api

• `Private` **\_api**: *any*

Defined in: [yajsapi/rest/market.ts:44](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L44)

___

### \_id

• `Private` **\_id**: *any*

Defined in: [yajsapi/rest/market.ts:46](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L46)

___

### \_subscription

• `Private` **\_subscription**: *any*

Defined in: [yajsapi/rest/market.ts:45](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L45)

## Methods

### confirm

▸ **confirm**(): *Promise*<*boolean*\>

**Returns:** *Promise*<*boolean*\>

Defined in: [yajsapi/rest/market.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L67)

___

### details

▸ **details**(): *Promise*<*AgreementDetails*\>

**Returns:** *Promise*<*AgreementDetails*\>

Defined in: [yajsapi/rest/market.ts:62](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L62)

___

### id

▸ **id**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/market.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L58)

___

### terminate

▸ **terminate**(`reason?`: *string*): *Promise*<*boolean*\>

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`reason` | *string* | "Finished" |

**Returns:** *Promise*<*boolean*\>

Defined in: [yajsapi/rest/market.ts:78](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/market.ts#L78)
