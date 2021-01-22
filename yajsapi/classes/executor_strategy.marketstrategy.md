[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / MarketStrategy

# Class: MarketStrategy

[executor/strategy](../modules/executor_strategy.md).MarketStrategy

## Hierarchy

* **MarketStrategy**

## Table of contents

### Constructors

- [constructor](executor_strategy.marketstrategy.md#constructor)

### Methods

- [decorate\_demand](executor_strategy.marketstrategy.md#decorate_demand)
- [score\_offer](executor_strategy.marketstrategy.md#score_offer)

## Constructors

### constructor

\+ **new MarketStrategy**(): [*MarketStrategy*](executor_strategy.marketstrategy.md)

**Returns:** [*MarketStrategy*](executor_strategy.marketstrategy.md)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`: [*DemandBuilder*](props_builder.demandbuilder.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`demand` | [*DemandBuilder*](props_builder.demandbuilder.md) |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/strategy.ts:25](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L25)

___

### score\_offer

▸ **score_offer**(`offer`: [*OfferProposal*](rest_market.offerproposal.md)): *Promise*<Number\>

#### Parameters:

Name | Type |
------ | ------ |
`offer` | [*OfferProposal*](rest_market.offerproposal.md) |

**Returns:** *Promise*<Number\>

Defined in: [yajsapi/executor/strategy.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L27)
