# executor

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/modules.md) / executor

## Module: executor

### Table of contents

#### References

* [Task](executor.md#task)
* [TaskStatus](executor.md#taskstatus)

#### Classes

* [Executor](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor.executor-1.md)
* [NoPaymentAccountError](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor.nopaymentaccounterror.md)
* [\_BufferItem](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor._bufferitem.md)
* [\_ExecutorConfig](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor._executorconfig.md)

#### Type aliases

* [ExecutorOpts](executor.md#executoropts)

#### Variables

* [sgx](executor.md#sgx)
* [vm](executor.md#vm)

### References

#### Task

Re-exports: [Task](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor_task.task.md)

#### TaskStatus

Re-exports: [TaskStatus](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/enums/executor_task.taskstatus.md)

### Type aliases

#### ExecutorOpts

Ƭ **ExecutorOpts**: { `budget`: _string_ ; `driver?`: _string_ ; `event_consumer?`: [_default_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_YaEvent_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor_events.yaevent.md)\], _void_&gt; ; `max_workers?`: Number ; `network?`: _string_ ; `strategy?`: [_MarketStrategy_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor_strategy.marketstrategy.md) ; `subnet_tag?`: _string_ ; `task_package`: [_Package_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/package.package-1.md) ; `timeout?`: Number \| String }

**Type declaration:**

| Name | Type |
| :--- | :--- |
| `budget` | _string_ |
| `driver?` | _string_ |
| `event_consumer?` | [_default_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/interfaces/utils_callable.default.md)&lt;\[[_YaEvent_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor_events.yaevent.md)\], _void_&gt; |
| `max_workers?` | Number |
| `network?` | _string_ |
| `strategy?` | [_MarketStrategy_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/executor_strategy.marketstrategy.md) |
| `subnet_tag?` | _string_ |
| `task_package` | [_Package_](https://github.com/golemfactory/yagna-docs/tree/5f53a0b64a8fff4cb7197e9d14d2dca4bc451540/yajsapi/classes/package.package-1.md) |
| `timeout?` | Number \| String |

Defined in: [yajsapi/executor/index.ts:97](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L97)

### Variables

#### sgx

• `Const` **sgx**: [_package/sgx_](package_sgx.md)

Defined in: [yajsapi/executor/index.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L32)

Defined in: [yajsapi/index.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/index.ts#L8)

#### vm

• `Const` **vm**: [_package/vm_](package_vm.md)

Defined in: [yajsapi/executor/index.ts:33](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L33)

Defined in: [yajsapi/index.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/index.ts#L8)

