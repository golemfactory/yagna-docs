# Interface: MarketOptions

[market/service](../modules/market_service.md).MarketOptions

## Hierarchy

- [`DemandOptions`](market_demand.DemandOptions.md)

  ↳ **`MarketOptions`**

## Table of contents

### Properties

- [strategy](market_service.MarketOptions.md#strategy)
- [debitNotesAcceptanceTimeout](market_service.MarketOptions.md#debitnotesacceptancetimeout)
- [subnetTag](market_service.MarketOptions.md#subnettag)
- [yagnaOptions](market_service.MarketOptions.md#yagnaoptions)
- [marketTimeout](market_service.MarketOptions.md#markettimeout)
- [marketOfferExpiration](market_service.MarketOptions.md#marketofferexpiration)
- [logger](market_service.MarketOptions.md#logger)
- [maxOfferEvents](market_service.MarketOptions.md#maxofferevents)
- [offerFetchingInterval](market_service.MarketOptions.md#offerfetchinginterval)
- [proposalTimeout](market_service.MarketOptions.md#proposaltimeout)
- [eventTarget](market_service.MarketOptions.md#eventtarget)

## Properties

### strategy

• `Optional` **strategy**: [`MarketStrategy`](market_strategy.MarketStrategy.md)

Strategy used to choose best offer

#### Defined in

[yajsapi/market/service.ts:12](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/service.ts#L12)

___

### debitNotesAcceptanceTimeout

• `Optional` **debitNotesAcceptanceTimeout**: `number`

#### Defined in

[yajsapi/market/service.ts:13](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/service.ts#L13)

___

### subnetTag

• `Optional` **subnetTag**: `string`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[subnetTag](market_demand.DemandOptions.md#subnettag)

#### Defined in

[yajsapi/market/demand.ts:16](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L16)

___

### yagnaOptions

• `Optional` **yagnaOptions**: [`YagnaOptions`](../modules/executor_executor.md#yagnaoptions)

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[yagnaOptions](market_demand.DemandOptions.md#yagnaoptions)

#### Defined in

[yajsapi/market/demand.ts:17](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L17)

___

### marketTimeout

• `Optional` **marketTimeout**: `number`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[marketTimeout](market_demand.DemandOptions.md#markettimeout)

#### Defined in

[yajsapi/market/demand.ts:18](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L18)

___

### marketOfferExpiration

• `Optional` **marketOfferExpiration**: `number`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[marketOfferExpiration](market_demand.DemandOptions.md#marketofferexpiration)

#### Defined in

[yajsapi/market/demand.ts:19](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L19)

___

### logger

• `Optional` **logger**: [`Logger`](utils_logger.Logger.md)

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[logger](market_demand.DemandOptions.md#logger)

#### Defined in

[yajsapi/market/demand.ts:20](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L20)

___

### maxOfferEvents

• `Optional` **maxOfferEvents**: `number`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[maxOfferEvents](market_demand.DemandOptions.md#maxofferevents)

#### Defined in

[yajsapi/market/demand.ts:21](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L21)

___

### offerFetchingInterval

• `Optional` **offerFetchingInterval**: `number`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[offerFetchingInterval](market_demand.DemandOptions.md#offerfetchinginterval)

#### Defined in

[yajsapi/market/demand.ts:22](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L22)

___

### proposalTimeout

• `Optional` **proposalTimeout**: `number`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[proposalTimeout](market_demand.DemandOptions.md#proposaltimeout)

#### Defined in

[yajsapi/market/demand.ts:23](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L23)

___

### eventTarget

• `Optional` **eventTarget**: `EventTarget`

#### Inherited from

[DemandOptions](market_demand.DemandOptions.md).[eventTarget](market_demand.DemandOptions.md#eventtarget)

#### Defined in

[yajsapi/market/demand.ts:24](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L24)
