# executor/executor

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor](../yajsapi-2/executor.md) / Executor

## Class: Executor

[executor](../yajsapi-2/executor.md).Executor

Task executor

**`description`** Used to run tasks using the specified application package within providers' execution units.

### Hierarchy

* **Executor**

### Table of contents

#### Constructors

* [constructor](executor.executor-1.md#constructor)

#### Properties

* [\_activity\_api](executor.executor-1.md#_activity_api)
* [\_api\_config](executor.executor-1.md#_api_config)
* [\_budget\_allocations](executor.executor-1.md#_budget_allocations)
* [\_budget\_amount](executor.executor-1.md#_budget_amount)
* [\_cancellation\_token](executor.executor-1.md#_cancellation_token)
* [\_conf](executor.executor-1.md#_conf)
* [\_driver](executor.executor-1.md#_driver)
* [\_expires](executor.executor-1.md#_expires)
* [\_market\_api](executor.executor-1.md#_market_api)
* [\_network](executor.executor-1.md#_network)
* [\_payment\_api](executor.executor-1.md#_payment_api)
* [\_stack](executor.executor-1.md#_stack)
* [\_strategy](executor.executor-1.md#_strategy)
* [\_stream\_output](executor.executor-1.md#_stream_output)
* [\_subnet](executor.executor-1.md#_subnet)
* [\_task\_package](executor.executor-1.md#_task_package)
* [\_worker\_cancellation\_token](executor.executor-1.md#_worker_cancellation_token)
* [\_wrapped\_consumer](executor.executor-1.md#_wrapped_consumer)

#### Methods

* [\_allocation\_for\_invoice](executor.executor-1.md#_allocation_for_invoice)
* [\_create\_allocations](executor.executor-1.md#_create_allocations)
* [\_get\_common\_payment\_platforms](executor.executor-1.md#_get_common_payment_platforms)
* [done](executor.executor-1.md#done)
* [ready](executor.executor-1.md#ready)
* [submit](executor.executor-1.md#submit)

### Constructors

#### constructor

+ **new Executor**\(`__namedParameters`: [_ExecutorOpts_](../yajsapi-2/executor.md#executoropts)\): [_Executor_](executor.executor-1.md)

Create new executor

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | [_ExecutorOpts_](../yajsapi-2/executor.md#executoropts) |

**Returns:** [_Executor_](executor.executor-1.md)

Defined in: [yajsapi/executor/index.ts:134](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L134)

### Properties

#### \_activity\_api

• `Private` **\_activity\_api**: _any_

Defined in: [yajsapi/executor/index.ts:128](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L128)

#### \_api\_config

• `Private` **\_api\_config**: _any_

Defined in: [yajsapi/executor/index.ts:120](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L120)

#### \_budget\_allocations

• `Private` **\_budget\_allocations**: [_Allocation_](rest_payment.allocation.md)\[\]

Defined in: [yajsapi/executor/index.ts:126](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L126)

#### \_budget\_amount

• `Private` **\_budget\_amount**: _any_

Defined in: [yajsapi/executor/index.ts:125](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L125)

#### \_cancellation\_token

• `Private` **\_cancellation\_token**: [_default_](utils_cancellationtoken.default.md)

Defined in: [yajsapi/executor/index.ts:133](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L133)

#### \_conf

• `Private` **\_conf**: _any_

Defined in: [yajsapi/executor/index.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L123)

#### \_driver

• `Private` **\_driver**: _any_

Defined in: [yajsapi/executor/index.ts:116](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L116)

#### \_expires

• `Private` **\_expires**: _any_

Defined in: [yajsapi/executor/index.ts:124](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L124)

#### \_market\_api

• `Private` **\_market\_api**: _any_

Defined in: [yajsapi/executor/index.ts:129](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L129)

#### \_network

• `Private` **\_network**: _any_

Defined in: [yajsapi/executor/index.ts:117](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L117)

#### \_payment\_api

• `Private` **\_payment\_api**: _any_

Defined in: [yajsapi/executor/index.ts:130](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L130)

#### \_stack

• `Private` **\_stack**: _any_

Defined in: [yajsapi/executor/index.ts:121](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L121)

#### \_strategy

• `Private` **\_strategy**: _any_

Defined in: [yajsapi/executor/index.ts:119](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L119)

#### \_stream\_output

• `Private` **\_stream\_output**: _any_

Defined in: [yajsapi/executor/index.ts:118](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L118)

#### \_subnet

• `Private` **\_subnet**: _any_

Defined in: [yajsapi/executor/index.ts:115](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L115)

#### \_task\_package

• `Private` **\_task\_package**: _any_

Defined in: [yajsapi/executor/index.ts:122](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L122)

#### \_worker\_cancellation\_token

• `Private` **\_worker\_cancellation\_token**: [_default_](utils_cancellationtoken.default.md)

Defined in: [yajsapi/executor/index.ts:134](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L134)

#### \_wrapped\_consumer

• `Private` **\_wrapped\_consumer**: _any_

Defined in: [yajsapi/executor/index.ts:132](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L132)

### Methods

#### \_allocation\_for\_invoice

▸ **\_allocation\_for\_invoice**\(`invoice`: [_Invoice_](rest_payment.invoice.md)\): [_Allocation_](rest_payment.allocation.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `invoice` | [_Invoice_](rest_payment.invoice.md) |

**Returns:** [_Allocation_](rest_payment.allocation.md)

Defined in: [yajsapi/executor/index.ts:788](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L788)

#### \_create\_allocations

▸ **\_create\_allocations**\(\): _Promise_

**Returns:** _Promise_

Defined in: [yajsapi/executor/index.ts:737](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L737)

#### \_get\_common\_payment\_platforms

▸ **\_get\_common\_payment\_platforms**\(`proposal`: [_OfferProposal_](rest_market.offerproposal.md)\): _string_\[\]

**Parameters:**

| Name | Type |
| :--- | :--- |
| `proposal` | [_OfferProposal_](rest_market.offerproposal.md) |

**Returns:** _string_\[\]

Defined in: [yajsapi/executor/index.ts:769](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L769)

#### done

▸ **done**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/executor/index.ts:820](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L820)

#### ready

▸ **ready**\(\): _Promise_&lt;[_Executor_](executor.executor-1.md)&gt;

**Returns:** _Promise_&lt;[_Executor_](executor.executor-1.md)&gt;

Defined in: [yajsapi/executor/index.ts:802](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L802)

#### submit

▸ **submit**\(`worker`: [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_WorkContext_](executor_ctx.workcontext.md), _AsyncIterable_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;&gt;\], _AsyncGenerator_&lt;[_Work_](executor_ctx.work.md), _any_, _unknown_&gt;&gt;, `data`: _Iterable_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;&gt;\): _AsyncGenerator_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;, _any_, _unknown_&gt;

Submit a computation to be executed on providers.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `worker` | [_default_](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_WorkContext_](executor_ctx.workcontext.md), _AsyncIterable_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;&gt;\], _AsyncGenerator_&lt;[_Work_](executor_ctx.work.md), _any_, _unknown_&gt;&gt; | a callable that takes a WorkContext object and a list o tasks, adds commands to the context object and yields committed commands |
| `data` | _Iterable_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;&gt; | an iterator of Task objects to be computed on providers |

**Returns:** _AsyncGenerator_&lt;[_Task_](executor_task.task.md)&lt;_D_, _R_&gt;, _any_, _unknown_&gt;

yields computation progress events

Defined in: [yajsapi/executor/index.ts:204](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L204)

