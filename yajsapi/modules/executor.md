# Module: executor

[yajsapi](../yajsapi.md) / [Exports](./) / executor

## Module: executor

### Table of contents

#### References

* [Task](executor.md#task)
* [TaskStatus](executor.md#taskstatus)

#### Classes

* [BatchResults](../classes/executor.batchresults.md)
* [Executor](../classes/executor.executor-1.md)
* [NoPaymentAccountError](../classes/executor.nopaymentaccounterror.md)
* [SubmissionState](../classes/executor.submissionstate.md)
* [\_ExecutorConfig](../classes/executor._executorconfig.md)

#### Type aliases

* [ExecutorOpts](executor.md#executoropts)

#### Variables

* [sgx](executor.md#sgx)
* [vm](executor.md#vm)

### References

#### Task

Re-exports: [Task](../classes/executor_task.task.md)

#### TaskStatus

Re-exports: [TaskStatus](../enumeration/executor_task.taskstatus.md)

### Type aliases

#### ExecutorOpts

Ƭ **ExecutorOpts**: `Object`

**Type declaration**

| Name | Type |
| :--- | :--- |
| `budget` | `string` |
| `driver?` | `string` |
| `event_consumer?` | [default](../interfaces/utils_callable.default.md)&lt;\[[YaEvent](../classes/executor_events.yaevent.md)\], void&gt; |
| `max_workers?` | `Number` |
| `network?` | `string` |
| `strategy?` | [MarketStrategy](../classes/executor_strategy.marketstrategy.md) |
| `subnet_tag?` | `string` |
| `task_package` | [Package](../classes/package.package-1.md) |
| `timeout?` | `Number` \| `String` |

**Defined in**

[yajsapi/executor/index.ts:115](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L115)

### Variables

#### sgx

• `Const` **sgx**: [package/sgx](package_sgx.md)

**Defined in**

[yajsapi/executor/index.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L38)

#### vm

• `Const` **vm**: [package/vm](package_vm.md)

**Defined in**

[yajsapi/executor/index.ts:39](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L39)

