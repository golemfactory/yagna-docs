# Class: NoPaymentAccountError

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor](../modules/executor.md) / NoPaymentAccountError

## Class: NoPaymentAccountError

[executor](../modules/executor.md).NoPaymentAccountError

### Hierarchy

* _Error_

  ↳ **NoPaymentAccountError**

### Table of contents

#### Constructors

* [constructor](executor.nopaymentaccounterror.md#constructor)

#### Properties

* [message](executor.nopaymentaccounterror.md#message)
* [name](executor.nopaymentaccounterror.md#name)
* [required\_driver](executor.nopaymentaccounterror.md#required_driver)
* [required\_network](executor.nopaymentaccounterror.md#required_network)
* [stack](executor.nopaymentaccounterror.md#stack)
* [prepareStackTrace](executor.nopaymentaccounterror.md#preparestacktrace)
* [stackTraceLimit](executor.nopaymentaccounterror.md#stacktracelimit)

#### Methods

* [toString](executor.nopaymentaccounterror.md#tostring)
* [captureStackTrace](executor.nopaymentaccounterror.md#capturestacktrace)

### Constructors

#### constructor

+ **new NoPaymentAccountError**\(`required_driver`: _any_, `required_network`: _any_\): [_NoPaymentAccountError_](executor.nopaymentaccounterror.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `required_driver` | _any_ |
| `required_network` | _any_ |

**Returns:** [_NoPaymentAccountError_](executor.nopaymentaccounterror.md)

Defined in: [yajsapi/executor/index.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L63)

### Properties

#### message

• **message**: _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:974

#### name

• **name**: _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:973

#### required\_driver

• **required\_driver**: _string_

Defined in: [yajsapi/executor/index.ts:61](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L61)

#### required\_network

• **required\_network**: _string_

Defined in: [yajsapi/executor/index.ts:63](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L63)

#### stack

• `Optional` **stack**: _undefined_ \| _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:975

#### prepareStackTrace

▪ `Optional` `Static` **prepareStackTrace**: _undefined_ \| \(`err`: Error, `stackTraces`: CallSite\[\]\) =&gt; _any_

Optional override for formatting stack traces

**`see`** [https://github.com/v8/v8/wiki/Stack Trace API\#customizing-stack-traces](https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces)

Defined in: node\_modules/@types/node/globals.d.ts:11

#### stackTraceLimit

▪ `Static` **stackTraceLimit**: _number_

Defined in: node\_modules/@types/node/globals.d.ts:13

### Methods

#### toString

▸ **toString**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/executor/index.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/index.ts#L71)

#### captureStackTrace

▸ `Static`**captureStackTrace**\(`targetObject`: _object_, `constructorOpt?`: Function\): _void_

Create .stack property on a target object

**Parameters:**

| Name | Type |
| :--- | :--- |
| `targetObject` | _object_ |
| `constructorOpt?` | Function |

**Returns:** _void_

Defined in: node\_modules/@types/node/globals.d.ts:4

