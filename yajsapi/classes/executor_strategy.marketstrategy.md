[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / MarketStrategy

# Class: MarketStrategy

[executor/strategy](../modules/executor_strategy.md).MarketStrategy

## Table of contents

### Constructors

- [constructor](executor_strategy.marketstrategy.md#constructor)

### Methods

- [decorate\_demand](executor_strategy.marketstrategy.md#decorate_demand)
- [score\_offer](executor_strategy.marketstrategy.md#score_offer)

## Constructors

### constructor

• **new MarketStrategy**()

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `demand` | [DemandBuilder](props_builder.demandbuilder.md) |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/strategy.ts:24](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L24)

___

### score\_offer

▸ **score_offer**(`offer`, `history?`): `Promise`<Number\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `offer` | [OfferProposal](rest_market.offerproposal.md) |
| `history?` | [ComputationHistory](../interfaces/executor_strategy.computationhistory.md) |

#### Returns

`Promise`<Number\>

#### Defined in

[yajsapi/executor/strategy.ts:26](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L26)
