[yajsapi](../README.md) / [Exports](../modules.md) / [executor](../modules/executor.md) / Executor

# Class: Executor

[executor](../modules/executor.md).Executor

Task executor

**`description`** Used to run tasks using the specified application package within providers' execution units.

## Table of contents

### Constructors

- [constructor](executor.executor-1.md#constructor)

### Properties

- [\_active\_computations](executor.executor-1.md#_active_computations)
- [\_activity\_api](executor.executor-1.md#_activity_api)
- [\_api\_config](executor.executor-1.md#_api_config)
- [\_budget\_allocations](executor.executor-1.md#_budget_allocations)
- [\_budget\_amount](executor.executor-1.md#_budget_amount)
- [\_cancellation\_token](executor.executor-1.md#_cancellation_token)
- [\_chan\_computation\_done](executor.executor-1.md#_chan_computation_done)
- [\_conf](executor.executor-1.md#_conf)
- [\_driver](executor.executor-1.md#_driver)
- [\_expires](executor.executor-1.md#_expires)
- [\_market\_api](executor.executor-1.md#_market_api)
- [\_network](executor.executor-1.md#_network)
- [\_payment\_api](executor.executor-1.md#_payment_api)
- [\_stack](executor.executor-1.md#_stack)
- [\_strategy](executor.executor-1.md#_strategy)
- [\_stream\_output](executor.executor-1.md#_stream_output)
- [\_subnet](executor.executor-1.md#_subnet)
- [\_task\_package](executor.executor-1.md#_task_package)
- [\_wrapped\_consumer](executor.executor-1.md#_wrapped_consumer)
- [state](executor.executor-1.md#state)

### Methods

- [\_create\_allocations](executor.executor-1.md#_create_allocations)
- [\_get\_allocation](executor.executor-1.md#_get_allocation)
- [\_get\_common\_payment\_platforms](executor.executor-1.md#_get_common_payment_platforms)
- [\_handle\_proposal](executor.executor-1.md#_handle_proposal)
- [\_submit](executor.executor-1.md#_submit)
- [done](executor.executor-1.md#done)
- [find\_offers](executor.executor-1.md#find_offers)
- [find\_offers\_for\_subscription](executor.executor-1.md#find_offers_for_subscription)
- [ready](executor.executor-1.md#ready)
- [submit](executor.executor-1.md#submit)

## Constructors

### constructor

• **new Executor**(`__namedParameters`)

Create new executor

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | [ExecutorOpts](../modules/executor.md#executoropts) |

#### Defined in

[yajsapi/executor/index.ts:168](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L168)

## Properties

### \_active\_computations

• `Private` **\_active\_computations**: `any`

#### Defined in

[yajsapi/executor/index.ts:166](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L166)

___

### \_activity\_api

• `Private` **\_activity\_api**: `any`

#### Defined in

[yajsapi/executor/index.ts:161](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L161)

___

### \_api\_config

• `Private` **\_api\_config**: `any`

#### Defined in

[yajsapi/executor/index.ts:151](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L151)

___

### \_budget\_allocations

• `Private` **\_budget\_allocations**: [Allocation](rest_payment.allocation.md)[]

#### Defined in

[yajsapi/executor/index.ts:157](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L157)

___

### \_budget\_amount

• `Private` **\_budget\_amount**: `any`

#### Defined in

[yajsapi/executor/index.ts:156](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L156)

___

### \_cancellation\_token

• `Private` **\_cancellation\_token**: [default](utils_cancellationtoken.default.md)

#### Defined in

[yajsapi/executor/index.ts:168](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L168)

___

### \_chan\_computation\_done

• `Private` **\_chan\_computation\_done**: `any`

#### Defined in

[yajsapi/executor/index.ts:167](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L167)

___

### \_conf

• `Private` **\_conf**: `any`

#### Defined in

[yajsapi/executor/index.ts:154](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L154)

___

### \_driver

• `Private` **\_driver**: `any`

#### Defined in

[yajsapi/executor/index.ts:147](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L147)

___

### \_expires

• `Private` **\_expires**: `any`

#### Defined in

[yajsapi/executor/index.ts:155](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L155)

___

### \_market\_api

• `Private` **\_market\_api**: `any`

#### Defined in

[yajsapi/executor/index.ts:162](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L162)

___

### \_network

• `Private` **\_network**: `any`

#### Defined in

[yajsapi/executor/index.ts:148](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L148)

___

### \_payment\_api

• `Private` **\_payment\_api**: `any`

#### Defined in

[yajsapi/executor/index.ts:163](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L163)

___

### \_stack

• `Private` **\_stack**: `any`

#### Defined in

[yajsapi/executor/index.ts:152](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L152)

___

### \_strategy

• `Private` **\_strategy**: `any`

#### Defined in

[yajsapi/executor/index.ts:150](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L150)

___

### \_stream\_output

• `Private` **\_stream\_output**: `any`

#### Defined in

[yajsapi/executor/index.ts:149](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L149)

___

### \_subnet

• `Private` **\_subnet**: `any`

#### Defined in

[yajsapi/executor/index.ts:146](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L146)

___

### \_task\_package

• `Private` **\_task\_package**: `any`

#### Defined in

[yajsapi/executor/index.ts:153](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L153)

___

### \_wrapped\_consumer

• `Private` **\_wrapped\_consumer**: `any`

#### Defined in

[yajsapi/executor/index.ts:165](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L165)

___

### state

• `Private` `Optional` **state**: [SubmissionState](executor.submissionstate.md)

#### Defined in

[yajsapi/executor/index.ts:159](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L159)

## Methods

### \_create\_allocations

▸ **_create_allocations**(): `Promise`<MarketDecoration\>

#### Returns

`Promise`<MarketDecoration\>

#### Defined in

[yajsapi/executor/index.ts:843](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L843)

___

### \_get\_allocation

▸ **_get_allocation**(`item`): [Allocation](rest_payment.allocation.md)

#### Parameters

| Name | Type |
| :------ | :------ |
| `item` | [Invoice](rest_payment.invoice.md) \| [DebitNote](rest_payment.debitnote.md) |

#### Returns

[Allocation](rest_payment.allocation.md)

#### Defined in

[yajsapi/executor/index.ts:894](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L894)

___

### \_get\_common\_payment\_platforms

▸ **_get_common_payment_platforms**(`proposal`): `string`[]

#### Parameters

| Name | Type |
| :------ | :------ |
| `proposal` | [OfferProposal](rest_market.offerproposal.md) |

#### Returns

`string`[]

#### Defined in

[yajsapi/executor/index.ts:875](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L875)

___

### \_handle\_proposal

▸ **_handle_proposal**(`state`, `proposal`): `Promise`<[ProposalEvent](executor_events.proposalevent.md)\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `state` | [SubmissionState](executor.submissionstate.md) |
| `proposal` | [OfferProposal](rest_market.offerproposal.md) |

#### Returns

`Promise`<[ProposalEvent](executor_events.proposalevent.md)\>

#### Defined in

[yajsapi/executor/index.ts:265](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L265)

___

### \_submit

▸ **_submit**(`worker`, `data`): `AsyncGenerator`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>, any, unknown\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `worker` | [default](../interfaces/utils_callable.default.md)<[[WorkContext](executor_ctx.workcontext.md), `AsyncIterable`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>\>], AsyncGenerator<WorkItem, any, [BatchResults](executor.batchresults.md)\>\> |
| `data` | `Iterable`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>\> |

#### Returns

`AsyncGenerator`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>, any, unknown\>

#### Defined in

[yajsapi/executor/index.ts:371](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L371)

___

### done

▸ **done**(): `Promise`<void\>

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/index.ts:926](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L926)

___

### find\_offers

▸ **find_offers**(`state`, `emit`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `state` | [SubmissionState](executor.submissionstate.md) |
| `emit` | [default](../interfaces/utils_callable.default.md)<[[YaEvent](executor_events.yaevent.md)], void\> |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/index.ts:347](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L347)

___

### find\_offers\_for\_subscription

▸ **find_offers_for_subscription**(`state`, `subscription`, `emit`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `state` | [SubmissionState](executor.submissionstate.md) |
| `subscription` | [Subscription](rest_market.subscription.md) |
| `emit` | [default](../interfaces/utils_callable.default.md)<[[YaEvent](executor_events.yaevent.md)], void\> |

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/executor/index.ts:310](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L310)

___

### ready

▸ **ready**(): `Promise`<[Executor](executor.executor-1.md)\>

#### Returns

`Promise`<[Executor](executor.executor-1.md)\>

#### Defined in

[yajsapi/executor/index.ts:908](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L908)

___

### submit

▸ **submit**(`worker`, `data`): `AsyncGenerator`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>, any, unknown\>

Submit a computation to be executed on providers.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `worker` | [default](../interfaces/utils_callable.default.md)<[[WorkContext](executor_ctx.workcontext.md), `AsyncIterable`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>\>], AsyncGenerator<WorkItem, any, [BatchResults](executor.batchresults.md)\>\> | a callable that takes a WorkContext object and a list o tasks, adds commands to the context object and yields committed commands |
| `data` | `Iterable`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>\> | an iterator of Task objects to be computed on providers |

#### Returns

`AsyncGenerator`<[Task](executor_task.task.md)<``"D"``, ``"R"``\>, any, unknown\>

yields computation progress events

#### Defined in

[yajsapi/executor/index.ts:247](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L247)
