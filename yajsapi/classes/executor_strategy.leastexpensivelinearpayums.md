[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / LeastExpensiveLinearPayuMS

# Class: LeastExpensiveLinearPayuMS

[executor/strategy](../modules/executor_strategy.md).LeastExpensiveLinearPayuMS

## Table of contents

### Constructors

- [constructor](executor_strategy.leastexpensivelinearpayums.md#constructor)

### Properties

- [\_expected\_time\_secs](executor_strategy.leastexpensivelinearpayums.md#_expected_time_secs)
- [\_max\_fixed\_price](executor_strategy.leastexpensivelinearpayums.md#_max_fixed_price)
- [\_max\_price\_for](executor_strategy.leastexpensivelinearpayums.md#_max_price_for)

### Methods

- [decorate\_demand](executor_strategy.leastexpensivelinearpayums.md#decorate_demand)
- [score\_offer](executor_strategy.leastexpensivelinearpayums.md#score_offer)

## Constructors

### constructor

• **new LeastExpensiveLinearPayuMS**(`expected_time_secs?`, `max_fixed_price?`, `max_price_for?`)

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `expected_time_secs` | `number` | 60 |
| `max_fixed_price?` | `number` | `undefined` |
| `max_price_for?` | `Map`<[Counter](../enums/props_com.counter.md), number\> | `undefined` |

#### Defined in

[yajsapi/executor/strategy.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L71)

## Properties

### \_expected\_time\_secs

• `Private` **\_expected\_time\_secs**: `number`

#### Defined in

[yajsapi/executor/strategy.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L69)

___

### \_max\_fixed\_price

• `Private` `Optional` **\_max\_fixed\_price**: `number`

#### Defined in

[yajsapi/executor/strategy.ts:70](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L70)

___

### \_max\_price\_for

• `Private` `Optional` **\_max\_price\_for**: `Map`<[Counter](../enums/props_com.counter.md), number\>

#### Defined in

[yajsapi/executor/strategy.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L71)

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

[yajsapi/executor/strategy.ts:83](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L83)

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

[yajsapi/executor/strategy.ts:87](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L87)
