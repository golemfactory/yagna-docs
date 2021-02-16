[yajsapi](../README.md) / [Exports](../modules.md) / [executor](../modules/executor.md) / NoPaymentAccountError

# Class: NoPaymentAccountError

[executor](../modules/executor.md).NoPaymentAccountError

## Hierarchy

* *Error*

  ↳ **NoPaymentAccountError**

## Table of contents

### Constructors

- [constructor](executor.nopaymentaccounterror.md#constructor)

### Properties

- [message](executor.nopaymentaccounterror.md#message)
- [name](executor.nopaymentaccounterror.md#name)
- [required\_driver](executor.nopaymentaccounterror.md#required_driver)
- [required\_network](executor.nopaymentaccounterror.md#required_network)
- [stack](executor.nopaymentaccounterror.md#stack)
- [prepareStackTrace](executor.nopaymentaccounterror.md#preparestacktrace)
- [stackTraceLimit](executor.nopaymentaccounterror.md#stacktracelimit)

### Methods

- [toString](executor.nopaymentaccounterror.md#tostring)
- [captureStackTrace](executor.nopaymentaccounterror.md#capturestacktrace)

## Constructors

### constructor

\+ **new NoPaymentAccountError**(`required_driver`: *any*, `required_network`: *any*): [*NoPaymentAccountError*](executor.nopaymentaccounterror.md)

#### Parameters:

Name | Type |
------ | ------ |
`required_driver` | *any* |
`required_network` | *any* |

**Returns:** [*NoPaymentAccountError*](executor.nopaymentaccounterror.md)

Defined in: [yajsapi/executor/index.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L63)

## Properties

### message

• **message**: *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:974

___

### name

• **name**: *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:973

___

### required\_driver

• **required\_driver**: *string*

Defined in: [yajsapi/executor/index.ts:61](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L61)

___

### required\_network

• **required\_network**: *string*

Defined in: [yajsapi/executor/index.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L63)

___

### stack

• `Optional` **stack**: *undefined* \| *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:975

___

### prepareStackTrace

▪ `Optional` `Static` **prepareStackTrace**: *undefined* \| (`err`: Error, `stackTraces`: CallSite[]) => *any*

Optional override for formatting stack traces

**`see`** https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces

Defined in: node_modules/@types/node/globals.d.ts:11

___

### stackTraceLimit

▪ `Static` **stackTraceLimit**: *number*

Defined in: node_modules/@types/node/globals.d.ts:13

## Methods

### toString

▸ **toString**(): *string*

**Returns:** *string*

Defined in: [yajsapi/executor/index.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L71)

___

### captureStackTrace

▸ `Static`**captureStackTrace**(`targetObject`: *object*, `constructorOpt?`: Function): *void*

Create .stack property on a target object

#### Parameters:

Name | Type |
------ | ------ |
`targetObject` | *object* |
`constructorOpt?` | Function |

**Returns:** *void*

Defined in: node_modules/@types/node/globals.d.ts:4
