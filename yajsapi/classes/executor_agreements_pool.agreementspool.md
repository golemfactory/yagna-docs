# Class: AgreementsPool

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/agreements\_pool](../modules/executor_agreements_pool.md) / AgreementsPool

## Class: AgreementsPool

[executor/agreements\_pool](../modules/executor_agreements_pool.md).AgreementsPool

### Implements

* [ComputationHistory](../interfaces/executor_strategy.computationhistory.md)

### Table of contents

#### Constructors

* [constructor](executor_agreements_pool.agreementspool.md#constructor)

#### Properties

* [\_agreements](executor_agreements_pool.agreementspool.md#_agreements)
* [\_confirmed](executor_agreements_pool.agreementspool.md#_confirmed)
* [\_lock](executor_agreements_pool.agreementspool.md#_lock)
* [\_offer\_buffer](executor_agreements_pool.agreementspool.md#_offer_buffer)
* [\_rejecting\_providers](executor_agreements_pool.agreementspool.md#_rejecting_providers)
* [cancellation\_token](executor_agreements_pool.agreementspool.md#cancellation_token)
* [emitter](executor_agreements_pool.agreementspool.md#emitter)

#### Methods

* [\_get\_agreement](executor_agreements_pool.agreementspool.md#_get_agreement)
* [\_set\_worker](executor_agreements_pool.agreementspool.md#_set_worker)
* [\_terminate\_agreement](executor_agreements_pool.agreementspool.md#_terminate_agreement)
* [add\_proposal](executor_agreements_pool.agreementspool.md#add_proposal)
* [cycle](executor_agreements_pool.agreementspool.md#cycle)
* [rejected\_last\_agreement](executor_agreements_pool.agreementspool.md#rejected_last_agreement)
* [release\_agreement](executor_agreements_pool.agreementspool.md#release_agreement)
* [terminate\_all](executor_agreements_pool.agreementspool.md#terminate_all)
* [use\_agreement](executor_agreements_pool.agreementspool.md#use_agreement)

### Constructors

#### constructor

• **new AgreementsPool**\(`emitter`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `emitter` | `any` |

**Defined in**

[yajsapi/executor/agreements\_pool.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L38)

### Properties

#### \_agreements

• `Private` **\_agreements**: `Map`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:34](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L34)

#### \_confirmed

• `Private` **\_confirmed**: `number` = 0

**Defined in**

[yajsapi/executor/agreements\_pool.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L37)

#### \_lock

• `Private` **\_lock**: [Lock](utils_lock.lock.md)

**Defined in**

[yajsapi/executor/agreements\_pool.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L35)

#### \_offer\_buffer

• `Private` **\_offer\_buffer**: `Map`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:33](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L33)

#### \_rejecting\_providers

• `Private` **\_rejecting\_providers**: `Set`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:36](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L36)

#### cancellation\_token

• `Optional` **cancellation\_token**: [default](utils_cancellationtoken.default.md)

**Defined in**

[yajsapi/executor/agreements\_pool.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L38)

#### emitter

• `Private` **emitter**: `any`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:32](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L32)

### Methods

#### \_get\_agreement

▸ `Private` **\_get\_agreement**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:75](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L75)

#### \_set\_worker

▸ **\_set\_worker**\(`agreement_id`, `task`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `agreement_id` | `string` |
| `task` | `any` |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L69)

#### \_terminate\_agreement

▸ `Private` **\_terminate\_agreement**\(`agreement_id`, `reason`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `agreement_id` | `string` |
| `reason` | `object` |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:156](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L156)

#### add\_proposal

▸ **add\_proposal**\(`score`, `proposal`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `score` | `number` |
| `proposal` | [OfferProposal](rest_market.offerproposal.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:53](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L53)

#### cycle

▸ **cycle**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:42](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L42)

#### rejected\_last\_agreement

▸ **rejected\_last\_agreement**\(`provider_id`\): `boolean`

**Parameters**

| Name | Type |
| :--- | :--- |
| `provider_id` | `string` |

**Returns**

`boolean`

**Implementation of**

ComputationHistory.rejected\_last\_agreement

**Defined in**

[yajsapi/executor/agreements\_pool.ts:187](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L187)

#### release\_agreement

▸ **release\_agreement**\(`agreement_id`, `allow_reuse?`\): `Promise`

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `agreement_id` | `string` | `undefined` |
| `allow_reuse` | `boolean` | true |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:144](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L144)

#### terminate\_all

▸ **terminate\_all**\(`reason`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `reason` | `object` |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:180](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L180)

#### use\_agreement

▸ **use\_agreement**\(`cbk`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `cbk` | `any` |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/agreements\_pool.ts:58](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/agreements_pool.ts#L58)

