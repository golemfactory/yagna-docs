[yajsapi](../README.md) / [Exports](../modules.md) / [executor/agreements_pool](../modules/executor_agreements_pool.md) / AgreementsPool

# Class: AgreementsPool

[executor/agreements_pool](../modules/executor_agreements_pool.md).AgreementsPool

## Implements

- [ComputationHistory](../interfaces/executor_strategy.computationhistory.md)

## Table of contents

### Constructors

- [constructor](executor_agreements_pool.agreementspool.md#constructor)

### Properties

- [\_agreements](executor_agreements_pool.agreementspool.md#_agreements)
- [\_confirmed](executor_agreements_pool.agreementspool.md#_confirmed)
- [\_lock](executor_agreements_pool.agreementspool.md#_lock)
- [\_offer\_buffer](executor_agreements_pool.agreementspool.md#_offer_buffer)
- [\_rejecting\_providers](executor_agreements_pool.agreementspool.md#_rejecting_providers)
- [cancellation\_token](executor_agreements_pool.agreementspool.md#cancellation_token)
- [emitter](executor_agreements_pool.agreementspool.md#emitter)

### Methods

- [\_get\_agreement](executor_agreements_pool.agreementspool.md#_get_agreement)
- [\_set\_worker](executor_agreements_pool.agreementspool.md#_set_worker)
- [\_terminate\_agreement](executor_agreements_pool.agreementspool.md#_terminate_agreement)
- [add\_proposal](executor_agreements_pool.agreementspool.md#add_proposal)
- [cycle](executor_agreements_pool.agreementspool.md#cycle)
- [rejected\_last\_agreement](executor_agreements_pool.agreementspool.md#rejected_last_agreement)
- [release\_agreement](executor_agreements_pool.agreementspool.md#release_agreement)
- [terminate\_all](executor_agreements_pool.agreementspool.md#terminate_all)
- [use\_agreement](executor_agreements_pool.agreementspool.md#use_agreement)

## Constructors

### constructor

• **new AgreementsPool**(`emitter`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `emitter` | `any` |

#### Defined in

[yajsapi/executor/agreements_pool.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L38)

## Properties

### \_agreements

• `Private` **\_agreements**: `Map`<string, BufferedAgreement\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:34](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L34)

___

### \_confirmed

• `Private` **\_confirmed**: `number` = 0

#### Defined in

[yajsapi/executor/agreements_pool.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L37)

___

### \_lock

• `Private` **\_lock**: [Lock](utils_lock.lock.md)

#### Defined in

[yajsapi/executor/agreements_pool.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L35)

___

### \_offer\_buffer

• `Private` **\_offer\_buffer**: `Map`<string, \_BufferedProposal\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:33](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L33)

___

### \_rejecting\_providers

• `Private` **\_rejecting\_providers**: `Set`<string\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:36](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L36)

___

### cancellation\_token

• `Optional` **cancellation\_token**: [default](utils_cancellationtoken.default.md)

#### Defined in

[yajsapi/executor/agreements_pool.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L38)

___

### emitter

• `Private` **emitter**: `any`

#### Defined in

[yajsapi/executor/agreements_pool.ts:32](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L32)

## Methods

### \_get\_agreement

▸ `Private` **_get_agreement**(): `Promise`<undefined \| [[Agreement](rest_market.agreement.md), [NodeInfo](props.nodeinfo.md)]\>

#### Returns

`Promise`<undefined \| [[Agreement](rest_market.agreement.md), [NodeInfo](props.nodeinfo.md)]\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:75](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L75)

___

### \_set\_worker

▸ **_set_worker**(`agreement_id`, `task`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `agreement_id` | `string` |
| `task` | `any` |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L69)

___

### \_terminate\_agreement

▸ `Private` **_terminate_agreement**(`agreement_id`, `reason`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `agreement_id` | `string` |
| `reason` | `object` |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:156](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L156)

___

### add\_proposal

▸ **add_proposal**(`score`, `proposal`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `score` | `number` |
| `proposal` | [OfferProposal](rest_market.offerproposal.md) |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:53](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L53)

___

### cycle

▸ **cycle**(): `Promise`<void\>

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L42)

___

### rejected\_last\_agreement

▸ **rejected_last_agreement**(`provider_id`): `boolean`

#### Parameters

| Name | Type |
| :------ | :------ |
| `provider_id` | `string` |

#### Returns

`boolean`

#### Implementation of

ComputationHistory.rejected\_last\_agreement

#### Defined in

[yajsapi/executor/agreements_pool.ts:187](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L187)

___

### release\_agreement

▸ **release_agreement**(`agreement_id`, `allow_reuse?`): `Promise`<void\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `agreement_id` | `string` | `undefined` |
| `allow_reuse` | `boolean` | true |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:144](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L144)

___

### terminate\_all

▸ **terminate_all**(`reason`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `reason` | `object` |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:180](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L180)

___

### use\_agreement

▸ **use_agreement**(`cbk`): `Promise`<any\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `cbk` | `any` |

#### Returns

`Promise`<any\>

#### Defined in

[yajsapi/executor/agreements_pool.ts:58](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L58)
