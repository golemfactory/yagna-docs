# Class: MarketStrategy

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / MarketStrategy

## Class: MarketStrategy

[executor/strategy](../modules/executor_strategy.md).MarketStrategy

### Hierarchy

* **MarketStrategy**

### Table of contents

#### Constructors

* [constructor](executor_strategy.marketstrategy.md#constructor)

#### Methods

* [decorate\_demand](executor_strategy.marketstrategy.md#decorate_demand)
* [score\_offer](executor_strategy.marketstrategy.md#score_offer)

### Constructors

#### constructor

* **new MarketStrategy**\(\): [_MarketStrategy_](executor_strategy.marketstrategy.md)

**Returns:** [_MarketStrategy_](executor_strategy.marketstrategy.md)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`: [_DemandBuilder_](props_builder.demandbuilder.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `demand` | [_DemandBuilder_](props_builder.demandbuilder.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/strategy.ts:25](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L25)

#### score\_offer

▸ **score\_offer**\(`offer`: [_OfferProposal_](rest_market.offerproposal.md)\): _Promise_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `offer` | [_OfferProposal_](rest_market.offerproposal.md) |

**Returns:** _Promise_

Defined in: [yajsapi/executor/strategy.ts:27](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L27)

