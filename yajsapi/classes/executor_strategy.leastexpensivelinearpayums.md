# Class: LeastExpensiveLinearPayuMS

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / LeastExpensiveLinearPayuMS

## Class: LeastExpensiveLinearPayuMS

[executor/strategy](../modules/executor_strategy.md).LeastExpensiveLinearPayuMS

### Hierarchy

* **LeastExpensiveLinearPayuMS**

### Table of contents

#### Constructors

* [constructor](executor_strategy.leastexpensivelinearpayums.md#constructor)

#### Properties

* [\_expected\_time\_secs](executor_strategy.leastexpensivelinearpayums.md#_expected_time_secs)

#### Methods

* [decorate\_demand](executor_strategy.leastexpensivelinearpayums.md#decorate_demand)
* [score\_offer](executor_strategy.leastexpensivelinearpayums.md#score_offer)

### Constructors

#### constructor

* **new LeastExpensiveLinearPayuMS**\(`expected_time_secs?`: _number_\): [_LeastExpensiveLinearPayuMS_](executor_strategy.leastexpensivelinearpayums.md)

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `expected_time_secs` | _number_ | 60 |

**Returns:** [_LeastExpensiveLinearPayuMS_](executor_strategy.leastexpensivelinearpayums.md)

Defined in: [yajsapi/executor/strategy.ts:67](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L67)

### Properties

#### \_expected\_time\_secs

• `Private` **\_expected\_time\_secs**: _number_

Defined in: [yajsapi/executor/strategy.ts:67](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L67)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`: [_DemandBuilder_](props_builder.demandbuilder.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `demand` | [_DemandBuilder_](props_builder.demandbuilder.md) |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/strategy.ts:72](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L72)

#### score\_offer

▸ **score\_offer**\(`offer`: [_OfferProposal_](rest_market.offerproposal.md)\): _Promise_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `offer` | [_OfferProposal_](rest_market.offerproposal.md) |

**Returns:** _Promise_

Defined in: [yajsapi/executor/strategy.ts:76](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/strategy.ts#L76)

