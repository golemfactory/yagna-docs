# Class: LeastExpensiveLinearPayuMS

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/strategy](../modules/executor_strategy.md) / LeastExpensiveLinearPayuMS

## Class: LeastExpensiveLinearPayuMS

[executor/strategy](../modules/executor_strategy.md).LeastExpensiveLinearPayuMS

### Table of contents

#### Constructors

* [constructor](executor_strategy.leastexpensivelinearpayums.md#constructor)

#### Properties

* [\_expected\_time\_secs](executor_strategy.leastexpensivelinearpayums.md#_expected_time_secs)
* [\_max\_fixed\_price](executor_strategy.leastexpensivelinearpayums.md#_max_fixed_price)
* [\_max\_price\_for](executor_strategy.leastexpensivelinearpayums.md#_max_price_for)

#### Methods

* [decorate\_demand](executor_strategy.leastexpensivelinearpayums.md#decorate_demand)
* [score\_offer](executor_strategy.leastexpensivelinearpayums.md#score_offer)

### Constructors

#### constructor

• **new LeastExpensiveLinearPayuMS**\(`expected_time_secs?`, `max_fixed_price?`, `max_price_for?`\)

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `expected_time_secs` | `number` | 60 |
| `max_fixed_price?` | `number` | `undefined` |
| `max_price_for?` | `Map`&lt;[Counter](../enumeration/props_com.counter.md), number&gt; | `undefined` |

**Defined in**

[yajsapi/executor/strategy.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L71)

### Properties

#### \_expected\_time\_secs

• `Private` **\_expected\_time\_secs**: `number`

**Defined in**

[yajsapi/executor/strategy.ts:69](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L69)

#### \_max\_fixed\_price

• `Private` `Optional` **\_max\_fixed\_price**: `number`

**Defined in**

[yajsapi/executor/strategy.ts:70](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L70)

#### \_max\_price\_for

• `Private` `Optional` **\_max\_price\_for**: `Map`&lt;[Counter](../enumeration/props_com.counter.md), number&gt;

**Defined in**

[yajsapi/executor/strategy.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L71)

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

[yajsapi/executor/strategy.ts:83](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L83)

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

[yajsapi/executor/strategy.ts:87](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/strategy.ts#L87)

