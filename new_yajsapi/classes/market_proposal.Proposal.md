# Class: Proposal

[market/proposal](../modules/market_proposal.md).Proposal

## Table of contents

### Constructors

- [constructor](market_proposal.Proposal.md#constructor)

### Properties

- [id](market_proposal.Proposal.md#id)
- [issuerId](market_proposal.Proposal.md#issuerid)
- [properties](market_proposal.Proposal.md#properties)
- [constraints](market_proposal.Proposal.md#constraints)
- [timestamp](market_proposal.Proposal.md#timestamp)

### Accessors

- [score](market_proposal.Proposal.md#score)

### Methods

- [isInitial](market_proposal.Proposal.md#isinitial)
- [isDraft](market_proposal.Proposal.md#isdraft)
- [isExpired](market_proposal.Proposal.md#isexpired)
- [isRejected](market_proposal.Proposal.md#isrejected)
- [reject](market_proposal.Proposal.md#reject)
- [respond](market_proposal.Proposal.md#respond)

## Constructors

### constructor

• **new Proposal**(`subscriptionId`, `api`, `model`, `demandRequest`, `eventTarget?`)

Create proposal for given subscription ID

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `subscriptionId` | `string` | subscription ID |
| `api` | `RequestorApi` | RequestorApi |
| `model` | `Proposal` | ProposalModel |
| `demandRequest` | `DemandOfferBase` | DemandOfferBase |
| `eventTarget?` | `EventTarget` | EventTarget |

#### Defined in

[yajsapi/market/proposal.ts:28](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L28)

## Properties

### id

• `Readonly` **id**: `string`

#### Defined in

[yajsapi/market/proposal.ts:10](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L10)

___

### issuerId

• `Readonly` **issuerId**: `string`

#### Defined in

[yajsapi/market/proposal.ts:11](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L11)

___

### properties

• `Readonly` **properties**: `object`

#### Defined in

[yajsapi/market/proposal.ts:12](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L12)

___

### constraints

• `Readonly` **constraints**: `string`

#### Defined in

[yajsapi/market/proposal.ts:13](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L13)

___

### timestamp

• `Readonly` **timestamp**: `string`

#### Defined in

[yajsapi/market/proposal.ts:14](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L14)

## Accessors

### score

• `get` **score**(): ``null`` \| `number`

#### Returns

``null`` \| `number`

#### Defined in

[yajsapi/market/proposal.ts:48](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L48)

• `set` **score**(`score`): `void`

#### Parameters

| Name | Type |
| :------ | :------ |
| `score` | ``null`` \| `number` |

#### Returns

`void`

#### Defined in

[yajsapi/market/proposal.ts:44](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L44)

## Methods

### isInitial

▸ **isInitial**(): `boolean`

#### Returns

`boolean`

#### Defined in

[yajsapi/market/proposal.ts:52](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L52)

___

### isDraft

▸ **isDraft**(): `boolean`

#### Returns

`boolean`

#### Defined in

[yajsapi/market/proposal.ts:56](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L56)

___

### isExpired

▸ **isExpired**(): `boolean`

#### Returns

`boolean`

#### Defined in

[yajsapi/market/proposal.ts:60](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L60)

___

### isRejected

▸ **isRejected**(): `boolean`

#### Returns

`boolean`

#### Defined in

[yajsapi/market/proposal.ts:64](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L64)

___

### reject

▸ **reject**(`reason?`): `Promise`<`void`\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `reason` | `string` | `"no reason"` |

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/market/proposal.ts:68](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L68)

___

### respond

▸ **respond**(`chosenPlatform`): `Promise`<`void`\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `chosenPlatform` | `any` |

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/market/proposal.ts:76](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/proposal.ts#L76)
