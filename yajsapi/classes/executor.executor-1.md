[yajsapi](../README.md) / [Exports](../modules.md) / [executor](../modules/executor.md) / Executor

# Class: Executor

[executor](../modules/executor.md).Executor

Task executor

**`description`** Used to run tasks using the specified application package within providers' execution units.

## Hierarchy

* **Executor**

## Table of contents

### Constructors

- [constructor](executor.executor-1.md#constructor)

### Properties

- [\_activity\_api](executor.executor-1.md#_activity_api)
- [\_api\_config](executor.executor-1.md#_api_config)
- [\_budget\_allocations](executor.executor-1.md#_budget_allocations)
- [\_budget\_amount](executor.executor-1.md#_budget_amount)
- [\_cancellation\_token](executor.executor-1.md#_cancellation_token)
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
- [\_worker\_cancellation\_token](executor.executor-1.md#_worker_cancellation_token)
- [\_wrapped\_consumer](executor.executor-1.md#_wrapped_consumer)

### Methods

- [\_allocation\_for\_invoice](executor.executor-1.md#_allocation_for_invoice)
- [\_create\_allocations](executor.executor-1.md#_create_allocations)
- [\_get\_common\_payment\_platforms](executor.executor-1.md#_get_common_payment_platforms)
- [done](executor.executor-1.md#done)
- [ready](executor.executor-1.md#ready)
- [submit](executor.executor-1.md#submit)

## Constructors

### constructor

\+ **new Executor**(`__namedParameters`: [*ExecutorOpts*](../modules/executor.md#executoropts)): [*Executor*](executor.executor-1.md)

Create new executor

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | [*ExecutorOpts*](../modules/executor.md#executoropts) |

**Returns:** [*Executor*](executor.executor-1.md)

Defined in: [yajsapi/executor/index.ts:134](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L134)

## Properties

### \_activity\_api

• `Private` **\_activity\_api**: *any*

Defined in: [yajsapi/executor/index.ts:128](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L128)

___

### \_api\_config

• `Private` **\_api\_config**: *any*

Defined in: [yajsapi/executor/index.ts:120](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L120)

___

### \_budget\_allocations

• `Private` **\_budget\_allocations**: [*Allocation*](rest_payment.allocation.md)[]

Defined in: [yajsapi/executor/index.ts:126](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L126)

___

### \_budget\_amount

• `Private` **\_budget\_amount**: *any*

Defined in: [yajsapi/executor/index.ts:125](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L125)

___

### \_cancellation\_token

• `Private` **\_cancellation\_token**: [*default*](utils_cancellationtoken.default.md)

Defined in: [yajsapi/executor/index.ts:133](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L133)

___

### \_conf

• `Private` **\_conf**: *any*

Defined in: [yajsapi/executor/index.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L123)

___

### \_driver

• `Private` **\_driver**: *any*

Defined in: [yajsapi/executor/index.ts:116](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L116)

___

### \_expires

• `Private` **\_expires**: *any*

Defined in: [yajsapi/executor/index.ts:124](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L124)

___

### \_market\_api

• `Private` **\_market\_api**: *any*

Defined in: [yajsapi/executor/index.ts:129](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L129)

___

### \_network

• `Private` **\_network**: *any*

Defined in: [yajsapi/executor/index.ts:117](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L117)

___

### \_payment\_api

• `Private` **\_payment\_api**: *any*

Defined in: [yajsapi/executor/index.ts:130](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L130)

___

### \_stack

• `Private` **\_stack**: *any*

Defined in: [yajsapi/executor/index.ts:121](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L121)

___

### \_strategy

• `Private` **\_strategy**: *any*

Defined in: [yajsapi/executor/index.ts:119](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L119)

___

### \_stream\_output

• `Private` **\_stream\_output**: *any*

Defined in: [yajsapi/executor/index.ts:118](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L118)

___

### \_subnet

• `Private` **\_subnet**: *any*

Defined in: [yajsapi/executor/index.ts:115](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L115)

___

### \_task\_package

• `Private` **\_task\_package**: *any*

Defined in: [yajsapi/executor/index.ts:122](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L122)

___

### \_worker\_cancellation\_token

• `Private` **\_worker\_cancellation\_token**: [*default*](utils_cancellationtoken.default.md)

Defined in: [yajsapi/executor/index.ts:134](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L134)

___

### \_wrapped\_consumer

• `Private` **\_wrapped\_consumer**: *any*

Defined in: [yajsapi/executor/index.ts:132](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L132)

## Methods

### \_allocation\_for\_invoice

▸ **_allocation_for_invoice**(`invoice`: [*Invoice*](rest_payment.invoice.md)): [*Allocation*](rest_payment.allocation.md)

#### Parameters:

Name | Type |
------ | ------ |
`invoice` | [*Invoice*](rest_payment.invoice.md) |

**Returns:** [*Allocation*](rest_payment.allocation.md)

Defined in: [yajsapi/executor/index.ts:788](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L788)

___

### \_create\_allocations

▸ **_create_allocations**(): *Promise*<MarketDecoration\>

**Returns:** *Promise*<MarketDecoration\>

Defined in: [yajsapi/executor/index.ts:737](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L737)

___

### \_get\_common\_payment\_platforms

▸ **_get_common_payment_platforms**(`proposal`: [*OfferProposal*](rest_market.offerproposal.md)): *string*[]

#### Parameters:

Name | Type |
------ | ------ |
`proposal` | [*OfferProposal*](rest_market.offerproposal.md) |

**Returns:** *string*[]

Defined in: [yajsapi/executor/index.ts:769](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L769)

___

### done

▸ **done**(): *Promise*<*void*\>

**Returns:** *Promise*<*void*\>

Defined in: [yajsapi/executor/index.ts:820](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L820)

___

### ready

▸ **ready**(): *Promise*<[*Executor*](executor.executor-1.md)\>

**Returns:** *Promise*<[*Executor*](executor.executor-1.md)\>

Defined in: [yajsapi/executor/index.ts:802](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L802)

___

### submit

▸ **submit**(`worker`: [*default*](../interfaces/utils_callable.default.md)<[[*WorkContext*](executor_ctx.workcontext.md), *AsyncIterable*<[*Task*](executor_task.task.md)<*D*, *R*\>\>], *AsyncGenerator*<[*Work*](executor_ctx.work.md), *any*, *unknown*\>\>, `data`: *Iterable*<[*Task*](executor_task.task.md)<*D*, *R*\>\>): *AsyncGenerator*<[*Task*](executor_task.task.md)<*D*, *R*\>, *any*, *unknown*\>

Submit a computation to be executed on providers.

#### Parameters:

Name | Type | Description |
------ | ------ | ------ |
`worker` | [*default*](../interfaces/utils_callable.default.md)<[[*WorkContext*](executor_ctx.workcontext.md), *AsyncIterable*<[*Task*](executor_task.task.md)<*D*, *R*\>\>], *AsyncGenerator*<[*Work*](executor_ctx.work.md), *any*, *unknown*\>\> | a callable that takes a WorkContext object and a list o tasks, adds commands to the context object and yields committed commands   |
`data` | *Iterable*<[*Task*](executor_task.task.md)<*D*, *R*\>\> | an iterator of Task objects to be computed on providers   |

**Returns:** *AsyncGenerator*<[*Task*](executor_task.task.md)<*D*, *R*\>, *any*, *unknown*\>

yields computation progress events

Defined in: [yajsapi/executor/index.ts:204](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L204)
