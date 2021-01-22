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
- [prepareStackTrace](executor.nopaymentaccounterror.md#preparestacktrace)
- [required\_driver](executor.nopaymentaccounterror.md#required_driver)
- [required\_network](executor.nopaymentaccounterror.md#required_network)
- [stack](executor.nopaymentaccounterror.md#stack)
- [stackTraceLimit](executor.nopaymentaccounterror.md#stacktracelimit)

### Methods

- [captureStackTrace](executor.nopaymentaccounterror.md#capturestacktrace)
- [toString](executor.nopaymentaccounterror.md#tostring)

## Constructors

### constructor

\+ **new NoPaymentAccountError**(`required_driver`: *any*, `required_network`: *any*): [*NoPaymentAccountError*](executor.nopaymentaccounterror.md)

#### Parameters:

Name | Type |
------ | ------ |
`required_driver` | *any* |
`required_network` | *any* |

**Returns:** [*NoPaymentAccountError*](executor.nopaymentaccounterror.md)

Defined in: [yajsapi/executor/index.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L58)

## Properties

### message

• **message**: *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:974

___

### name

• **name**: *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:973

___

### prepareStackTrace

• `Optional` **prepareStackTrace**: *undefined* \| (`err`: Error, `stackTraces`: CallSite[]) => *any*

Optional override for formatting stack traces

**`see`** https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces

Defined in: node_modules/@types/node/globals.d.ts:11

___

### required\_driver

• **required\_driver**: *string*

Defined in: [yajsapi/executor/index.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L56)

___

### required\_network

• **required\_network**: *string*

Defined in: [yajsapi/executor/index.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L58)

___

### stack

• `Optional` **stack**: *undefined* \| *string*

Defined in: node_modules/typescript/lib/lib.es5.d.ts:975

___

### stackTraceLimit

• **stackTraceLimit**: *number*

Defined in: node_modules/@types/node/globals.d.ts:13

## Methods

### captureStackTrace

▸ **captureStackTrace**(`targetObject`: *object*, `constructorOpt?`: Function): *void*

Create .stack property on a target object

#### Parameters:

Name | Type |
------ | ------ |
`targetObject` | *object* |
`constructorOpt?` | Function |

**Returns:** *void*

Defined in: node_modules/@types/node/globals.d.ts:4

___

### toString

▸ **toString**(): *string*

**Returns:** *string*

Defined in: [yajsapi/executor/index.ts:66](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L66)
