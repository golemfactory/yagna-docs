[yajsapi](../README.md) / [Exports](../modules.md) / [rest/activity](../modules/rest_activity.md) / Activity

# Class: Activity

[rest/activity](../modules/rest_activity.md).Activity

## Table of contents

### Constructors

- [constructor](rest_activity.activity.md#constructor)

### Properties

- [\_api](rest_activity.activity.md#_api)
- [\_credentials](rest_activity.activity.md#_credentials)
- [\_id](rest_activity.activity.md#_id)
- [\_state](rest_activity.activity.md#_state)

### Accessors

- [credentials](rest_activity.activity.md#credentials)
- [exeunitHashes](rest_activity.activity.md#exeunithashes)
- [id](rest_activity.activity.md#id)

### Methods

- [done](rest_activity.activity.md#done)
- [ready](rest_activity.activity.md#ready)
- [send](rest_activity.activity.md#send)
- [state](rest_activity.activity.md#state)

## Constructors

### constructor

• **new Activity**(`id`, `_api`, `_state`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `id` | `string` |
| `_api` | `RequestorControlApi` |
| `_state` | `RequestorStateApi` |

#### Defined in

[yajsapi/rest/activity.ts:161](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L161)

## Properties

### \_api

• `Protected` **\_api**: `RequestorControlApi`

#### Defined in

[yajsapi/rest/activity.ts:158](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L158)

___

### \_credentials

• `Protected` `Optional` **\_credentials**: `object`

#### Defined in

[yajsapi/rest/activity.ts:161](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L161)

___

### \_id

• `Protected` **\_id**: `string`

#### Defined in

[yajsapi/rest/activity.ts:160](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L160)

___

### \_state

• `Protected` **\_state**: `RequestorStateApi`

#### Defined in

[yajsapi/rest/activity.ts:159](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L159)

## Accessors

### credentials

• `get` **credentials**(): `undefined` \| `object`

#### Returns

`undefined` \| `object`

#### Defined in

[yajsapi/rest/activity.ts:181](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L181)

___

### exeunitHashes

• `get` **exeunitHashes**(): `undefined` \| `string`[]

#### Returns

`undefined` \| `string`[]

#### Defined in

[yajsapi/rest/activity.ts:185](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L185)

___

### id

• `get` **id**(): `string`

#### Returns

`string`

#### Defined in

[yajsapi/rest/activity.ts:177](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L177)

• `set` **id**(`x`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `x` | `string` |

#### Returns

`void`

#### Defined in

[yajsapi/rest/activity.ts:173](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L173)

## Methods

### done

▸ **done**(): `Promise`<void\>

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/rest/activity.ts:239](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L239)

___

### ready

▸ **ready**(): `Promise`<[Activity](rest_activity.activity.md)\>

#### Returns

`Promise`<[Activity](rest_activity.activity.md)\>

#### Defined in

[yajsapi/rest/activity.ts:235](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L235)

___

### send

▸ **send**(`script`, `stream`, `deadline?`, `cancellationToken?`): `Promise`<any\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `script` | `object`[] |
| `stream` | `boolean` |
| `deadline?` | `number` |
| `cancellationToken?` | [default](utils_cancellationtoken.default.md) |

#### Returns

`Promise`<any\>

#### Defined in

[yajsapi/rest/activity.ts:195](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L195)

___

### state

▸ **state**(): `Promise`<ActivityState\>

#### Returns

`Promise`<ActivityState\>

#### Defined in

[yajsapi/rest/activity.ts:189](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L189)
