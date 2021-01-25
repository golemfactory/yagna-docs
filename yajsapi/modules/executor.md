[yajsapi](../README.md) / [Exports](../modules.md) / executor

# Module: executor

## Table of contents

### References

- [Task](executor.md#task)
- [TaskStatus](executor.md#taskstatus)

### Classes

- [Executor](../classes/executor.executor-1.md)
- [NoPaymentAccountError](../classes/executor.nopaymentaccounterror.md)
- [\_BufferItem](../classes/executor._bufferitem.md)
- [\_ExecutorConfig](../classes/executor._executorconfig.md)

### Type aliases

- [ExecutorOpts](executor.md#executoropts)

### Variables

- [sgx](executor.md#sgx)
- [vm](executor.md#vm)

## References

### Task

Re-exports: [Task](../classes/executor_task.task.md)

___

### TaskStatus

Re-exports: [TaskStatus](../enums/executor_task.taskstatus.md)

## Type aliases

### ExecutorOpts

Ƭ **ExecutorOpts**: { `budget`: *string* ; `driver?`: *string* ; `event_consumer?`: [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](../classes/executor_events.yaevent.md)], *void*\> ; `max_workers?`: Number ; `network?`: *string* ; `strategy?`: [*MarketStrategy*](../classes/executor_strategy.marketstrategy.md) ; `subnet_tag?`: *string* ; `task_package`: [*Package*](../classes/package.package-1.md) ; `timeout?`: Number \| String  }

#### Type declaration:

Name | Type |
------ | ------ |
`budget` | *string* |
`driver?` | *string* |
`event_consumer?` | [*default*](../interfaces/utils_callable.default.md)<[[*YaEvent*](../classes/executor_events.yaevent.md)], *void*\> |
`max_workers?` | Number |
`network?` | *string* |
`strategy?` | [*MarketStrategy*](../classes/executor_strategy.marketstrategy.md) |
`subnet_tag?` | *string* |
`task_package` | [*Package*](../classes/package.package-1.md) |
`timeout?` | Number \| String |

Defined in: [yajsapi/executor/index.ts:97](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L97)

## Variables

### sgx

• `Const` **sgx**: [*package/sgx*](package_sgx.md)

Defined in: [yajsapi/executor/index.ts:32](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L32)

Defined in: [yajsapi/index.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/index.ts#L8)

___

### vm

• `Const` **vm**: [*package/vm*](package_vm.md)

Defined in: [yajsapi/executor/index.ts:33](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L33)

Defined in: [yajsapi/index.ts:8](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/index.ts#L8)
