# Class: MarketStrategy

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / MarketStrategy

## Class: MarketStrategy

[executor/strategy](../modules/executor_strategy.md).MarketStrategy

### Table of contents

#### Constructors

* [constructor](executor_strategy.marketstrategy.md#constructor)

#### Methods

* [decorate\_demand](executor_strategy.marketstrategy.md#decorate_demand)
* [score\_offer](executor_strategy.marketstrategy.md#score_offer)

### Constructors

#### constructor

• **new MarketStrategy**\(\)

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

[yajsapi/executor/strategy.ts:24](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L24)

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

[yajsapi/executor/strategy.ts:26](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L26)

