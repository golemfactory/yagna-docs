# Module: executor

[yajsapi](../yajsapi.md) / [Exports](./) / executor

## Module: executor

### Table of contents

#### References

* [Task](executor.md#task)
* [TaskStatus](executor.md#taskstatus)

#### Classes

* [Executor](../classes/executor.executor-1.md)
* [NoPaymentAccountError](../classes/executor.nopaymentaccounterror.md)
* [\_BufferItem](../classes/executor._bufferitem.md)
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

Ƭ **ExecutorOpts**: { `budget`: _string_ ; `driver?`: _string_ ; `event_consumer?`: [_default_](../interface/utils_callable.default.md)&lt;\[[_YaEvent_](../classes/executor_events.yaevent.md)\], _void_&gt; ; `max_workers?`: Number ; `network?`: _string_ ; `strategy?`: [_MarketStrategy_](../classes/executor_strategy.marketstrategy.md) ; `subnet_tag?`: _string_ ; `task_package`: [_Package_](../classes/package.package-1.md) ; `timeout?`: Number \| String }

**Type declaration:**

| Name | Type |
| :--- | :--- |
| `budget` | _string_ |
| `driver?` | _string_ |
| `event_consumer?` | [_default_](../interface/utils_callable.default.md)&lt;\[[_YaEvent_](../classes/executor_events.yaevent.md)\], _void_&gt; |
| `max_workers?` | Number |
| `network?` | _string_ |
| `strategy?` | [_MarketStrategy_](../classes/executor_strategy.marketstrategy.md) |
| `subnet_tag?` | _string_ |
| `task_package` | [_Package_](../classes/package.package-1.md) |
| `timeout?` | Number \| String |

Defined in: [yajsapi/executor/index.ts:102](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L102)

### Variables

#### sgx

• `Const` **sgx**: [_package/sgx_](package_sgx.md)

Defined in: [yajsapi/executor/index.ts:32](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L32)

Defined in: [yajsapi/index.ts:15](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/index.ts#L15)

#### vm

• `Const` **vm**: [_package/vm_](package_vm.md)

Defined in: [yajsapi/executor/index.ts:33](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L33)

Defined in: [yajsapi/index.ts:15](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/index.ts#L15)

