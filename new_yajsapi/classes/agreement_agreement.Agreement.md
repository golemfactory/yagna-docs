# Class: Agreement

[agreement/agreement](../modules/agreement_agreement.md).Agreement

## Table of contents

### Methods

- [create](agreement_agreement.Agreement.md#create)
- [refreshDetails](agreement_agreement.Agreement.md#refreshdetails)
- [getState](agreement_agreement.Agreement.md#getstate)
- [confirm](agreement_agreement.Agreement.md#confirm)
- [isFinalState](agreement_agreement.Agreement.md#isfinalstate)
- [terminate](agreement_agreement.Agreement.md#terminate)

### Properties

- [id](agreement_agreement.Agreement.md#id)
- [provider](agreement_agreement.Agreement.md#provider)

## Methods

### create

▸ `Static` **create**(`proposalId`, `agreementOptions?`): `Promise`<[`Agreement`](agreement_agreement.Agreement.md)\>

Create agreement for given proposal ID

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `proposalId` | `string` | proposal ID |
| `agreementOptions?` | [`AgreementOptions`](../interfaces/agreement_agreement.AgreementOptions.md) | [AgreementOptions](../interfaces/agreement_agreement.AgreementOptions.md) |

#### Returns

`Promise`<[`Agreement`](agreement_agreement.Agreement.md)\>

Agreement

#### Defined in

[yajsapi/agreement/agreement.ts:69](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L69)

___

### refreshDetails

▸ **refreshDetails**(): `Promise`<`void`\>

Refresh agreement details

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/agreement/agreement.ts:77](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L77)

___

### getState

▸ **getState**(): `Promise`<[`AgreementStateEnum`](../enums/agreement_agreement.AgreementStateEnum.md)\>

Return agreement state

#### Returns

`Promise`<[`AgreementStateEnum`](../enums/agreement_agreement.AgreementStateEnum.md)\>

state

#### Defined in

[yajsapi/agreement/agreement.ts:86](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L86)

___

### confirm

▸ **confirm**(): `Promise`<`void`\>

Confirm agreement and waits for provider approval

**`Description`**

Blocking function waits till agreement will be confirmed and approved by provider

**`Throws`**

Error if the agreement will be rejected by provider or failed to confirm

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/agreement/agreement.ts:96](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L96)

___

### isFinalState

▸ **isFinalState**(): `Promise`<`boolean`\>

Returns flag if the agreement is in the final state

**`Description`**

if the final state is true, agreement will not change state further anymore

#### Returns

`Promise`<`boolean`\>

boolean

#### Defined in

[yajsapi/agreement/agreement.ts:115](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L115)

___

### terminate

▸ **terminate**(`reason?`): `Promise`<`void`\>

Terminate agreement

**`Description`**

Blocking function waits till agreement will be terminated

**`Throws`**

Error if the agreement will be unable to terminate

#### Parameters

| Name | Type |
| :------ | :------ |
| `reason` | `Object` |

#### Returns

`Promise`<`void`\>

#### Defined in

[yajsapi/agreement/agreement.ts:125](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L125)

## Properties

### id

• `Readonly` **id**: `any`

agreement ID

#### Defined in

[yajsapi/agreement/agreement.ts:59](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L59)

___

### provider

• `Readonly` **provider**: [`ProviderInfo`](../interfaces/agreement_agreement.ProviderInfo.md)

[ProviderInfo](../interfaces/agreement_agreement.ProviderInfo.md)

#### Defined in

[yajsapi/agreement/agreement.ts:59](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/agreement/agreement.ts#L59)
