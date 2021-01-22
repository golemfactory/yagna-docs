[yajsapi](../README.md) / [Exports](../modules.md) / [executor/strategy](../modules/executor_strategy.md) / LeastExpensiveLinearPayuMS

# Class: LeastExpensiveLinearPayuMS

[executor/strategy](../modules/executor_strategy.md).LeastExpensiveLinearPayuMS

## Hierarchy

* **LeastExpensiveLinearPayuMS**

## Table of contents

### Constructors

- [constructor](executor_strategy.leastexpensivelinearpayums.md#constructor)

### Properties

- [\_expected\_time\_secs](executor_strategy.leastexpensivelinearpayums.md#_expected_time_secs)

### Methods

- [decorate\_demand](executor_strategy.leastexpensivelinearpayums.md#decorate_demand)
- [score\_offer](executor_strategy.leastexpensivelinearpayums.md#score_offer)

## Constructors

### constructor

\+ **new LeastExpensiveLinearPayuMS**(`expected_time_secs?`: *number*): [*LeastExpensiveLinearPayuMS*](executor_strategy.leastexpensivelinearpayums.md)

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`expected_time_secs` | *number* | 60 |

**Returns:** [*LeastExpensiveLinearPayuMS*](executor_strategy.leastexpensivelinearpayums.md)

Defined in: [yajsapi/executor/strategy.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L67)

## Properties

### \_expected\_time\_secs

• `Private` **\_expected\_time\_secs**: *number*

Defined in: [yajsapi/executor/strategy.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L67)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`: [*DemandBuilder*](props_builder.demandbuilder.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`demand` | [*DemandBuilder*](props_builder.demandbuilder.md) |

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/strategy.ts:72](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L72)

___

### score\_offer

▸ **score_offer**(`offer`: [*OfferProposal*](rest_market.offerproposal.md)): *Promise*<Number\>

#### Parameters:

Name | Type |
------ | ------ |
`offer` | [*OfferProposal*](rest_market.offerproposal.md) |

**Returns:** *Promise*<Number\>

Defined in: [yajsapi/executor/strategy.ts:76](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/strategy.ts#L76)
