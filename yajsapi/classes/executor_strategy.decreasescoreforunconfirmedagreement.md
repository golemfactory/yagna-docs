# Class: DecreaseScoreForUnconfirmedAgreement

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / DecreaseScoreForUnconfirmedAgreement

## Class: DecreaseScoreForUnconfirmedAgreement

[executor/strategy](../modules/executor_strategy.md).DecreaseScoreForUnconfirmedAgreement

### Table of contents

#### Constructors

* [constructor](executor_strategy.decreasescoreforunconfirmedagreement.md#constructor)

#### Properties

* [\_base\_strategy](executor_strategy.decreasescoreforunconfirmedagreement.md#_base_strategy)
* [\_factor](executor_strategy.decreasescoreforunconfirmedagreement.md#_factor)

#### Methods

* [decorate\_demand](executor_strategy.decreasescoreforunconfirmedagreement.md#decorate_demand)
* [score\_offer](executor_strategy.decreasescoreforunconfirmedagreement.md#score_offer)

### Constructors

#### constructor

• **new DecreaseScoreForUnconfirmedAgreement**\(`base_strategy`, `factor`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `base_strategy` | `any` |
| `factor` | `any` |

**Defined in**

[yajsapi/executor/strategy.ts:144](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L144)

### Properties

#### \_base\_strategy

• `Private` **\_base\_strategy**: `any`

**Defined in**

[yajsapi/executor/strategy.ts:143](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L143)

#### \_factor

• `Private` **\_factor**: `any`

**Defined in**

[yajsapi/executor/strategy.ts:144](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L144)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `demand` | [DemandBuilder](props_builder.demandbuilder.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/strategy.ts:151](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L151)

#### score\_offer

▸ **score\_offer**\(`offer`, `history?`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `offer` | [OfferProposal](rest_market.offerproposal.md) |
| `history?` | [ComputationHistory](../interfaces/executor_strategy.computationhistory.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/strategy.ts:156](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L156)

