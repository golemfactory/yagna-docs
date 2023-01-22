# Class: Activity

[activity/activity](../modules/activity_activity.md).Activity

## Table of contents

### Methods

- [create](activity_activity.Activity.md#create)
- [execute](activity_activity.Activity.md#execute)
- [stop](activity_activity.Activity.md#stop)
- [getState](activity_activity.Activity.md#getstate)
- [send](activity_activity.Activity.md#send)

### Properties

- [id](activity_activity.Activity.md#id)
- [agreementId](activity_activity.Activity.md#agreementid)
- [options](activity_activity.Activity.md#options)

## Methods

### create

▸ `Static` **create**(`agreementId`, `options?`, `secure?`): `Promise`<[`Activity`](activity_activity.Activity.md)\>

Create activity for given agreement ID

#### Parameters

| Name | Type | Default value | Description |
| :------ | :------ | :------ | :------ |
| `agreementId` | `string` | `undefined` |  |
| `options?` | [`ActivityOptions`](../interfaces/activity_activity.ActivityOptions.md) | `undefined` | [ActivityOptions](../interfaces/activity_activity.ActivityOptions.md) |
| `secure` | `boolean` | `false` | defines if activity will be secure type |

#### Returns

`Promise`<[`Activity`](activity_activity.Activity.md)\>

Activity

#### Defined in

[yajsapi/activity/activity.ts:74](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L74)

___

### execute

▸ **execute**(`script`, `stream?`, `timeout?`): `Promise`<`Readable`\>

Execute script

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `script` | [`ExeScriptRequest`](../interfaces/activity_activity.ExeScriptRequest.md) | exe script request |
| `stream?` | `boolean` | define type of getting results from execution (polling or streaming) |
| `timeout?` | `number` | execution timeout |

#### Returns

`Promise`<`Readable`\>

#### Defined in

[yajsapi/activity/activity.ts:86](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L86)

___

### stop

▸ **stop**(): `Promise`<`boolean`\>

Stop and destroy activity

#### Returns

`Promise`<`boolean`\>

boolean

#### Defined in

[yajsapi/activity/activity.ts:111](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L111)

___

### getState

▸ **getState**(): `Promise`<[`ActivityStateEnum`](../enums/activity_activity.ActivityStateEnum.md)\>

Getting current state of activity

**`Throws`**

Error when cannot query the state

#### Returns

`Promise`<[`ActivityStateEnum`](../enums/activity_activity.ActivityStateEnum.md)\>

state

#### Defined in

[yajsapi/activity/activity.ts:123](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L123)

___

### send

▸ `Protected` **send**(`script`): `Promise`<`string`\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `script` | [`ExeScriptRequest`](../interfaces/activity_activity.ExeScriptRequest.md) |

#### Returns

`Promise`<`string`\>

#### Defined in

[yajsapi/activity/activity.ts:134](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L134)

## Properties

### id

• `Readonly` **id**: `any`

activity ID

#### Defined in

[yajsapi/activity/activity.ts:62](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L62)

___

### agreementId

• `Readonly` **agreementId**: `any`

agreement ID

#### Defined in

[yajsapi/activity/activity.ts:62](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L62)

___

### options

• `Protected` `Readonly` **options**: `ActivityConfig`

[ActivityOptions](../interfaces/activity_activity.ActivityOptions.md)

#### Defined in

[yajsapi/activity/activity.ts:62](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/activity/activity.ts#L62)
