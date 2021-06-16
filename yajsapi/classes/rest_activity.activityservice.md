[yajsapi](../README.md) / [Exports](../modules.md) / [rest/activity](../modules/rest_activity.md) / ActivityService

# Class: ActivityService

[rest/activity](../modules/rest_activity.md).ActivityService

A convenience helper to facilitate the creation of an Activity.

## Table of contents

### Constructors

- [constructor](rest_activity.activityservice.md#constructor)

### Properties

- [\_api](rest_activity.activityservice.md#_api)
- [\_state](rest_activity.activityservice.md#_state)

### Methods

- [\_attest](rest_activity.activityservice.md#_attest)
- [\_create\_activity](rest_activity.activityservice.md#_create_activity)
- [\_create\_secure\_activity](rest_activity.activityservice.md#_create_secure_activity)
- [new\_activity](rest_activity.activityservice.md#new_activity)

## Constructors

### constructor

• **new ActivityService**(`cfg`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `cfg` | `Configuration` |

#### Defined in

[yajsapi/rest/activity.ts:29](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L29)

## Properties

### \_api

• `Private` **\_api**: `RequestorControlApi`

#### Defined in

[yajsapi/rest/activity.ts:28](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L28)

___

### \_state

• `Private` **\_state**: `RequestorStateApi`

#### Defined in

[yajsapi/rest/activity.ts:29](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L29)

## Methods

### \_attest

▸ **_attest**(`activity_id`, `agreement`, `credentials`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `activity_id` | `string` |
| `agreement` | [Agreement](rest_market.agreement.md) |
| `credentials` | `Credentials` |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/rest/activity.ts:110](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L110)

___

### \_create\_activity

▸ **_create_activity**(`agreement_id`): `Promise`<[Activity](rest_activity.activity.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `agreement_id` | `string` |

#### Returns

`Promise`<[Activity](rest_activity.activity.md)\>

#### Defined in

[yajsapi/rest/activity.ts:59](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L59)

___

### \_create\_secure\_activity

▸ **_create_secure_activity**(`agreement`): `Promise`<SecureActivity\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `agreement` | [Agreement](rest_market.agreement.md) |

#### Returns

`Promise`<SecureActivity\>

#### Defined in

[yajsapi/rest/activity.ts:67](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L67)

___

### new\_activity

▸ **new_activity**(`agreement`, `secure?`): `Promise`<[Activity](rest_activity.activity.md)\>

Create an activity within bounds of the specified agreement.

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `agreement` | [Agreement](rest_market.agreement.md) | `undefined` | - |
| `secure` | `boolean` | false | - |

#### Returns

`Promise`<[Activity](rest_activity.activity.md)\>

Activity

#### Defined in

[yajsapi/rest/activity.ts:43](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L43)
