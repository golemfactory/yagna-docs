# executor/nopaymentaccounterror

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor](../yajsapi-2/executor.md) / NoPaymentAccountError

## Class: NoPaymentAccountError

[executor](../yajsapi-2/executor.md).NoPaymentAccountError

### Hierarchy

* _Error_

  ↳ **NoPaymentAccountError**

### Table of contents

#### Constructors

* [constructor](executor.nopaymentaccounterror.md#constructor)

#### Properties

* [message](executor.nopaymentaccounterror.md#message)
* [name](executor.nopaymentaccounterror.md#name)
* [prepareStackTrace](executor.nopaymentaccounterror.md#preparestacktrace)
* [required\_driver](executor.nopaymentaccounterror.md#required_driver)
* [required\_network](executor.nopaymentaccounterror.md#required_network)
* [stack](executor.nopaymentaccounterror.md#stack)
* [stackTraceLimit](executor.nopaymentaccounterror.md#stacktracelimit)

#### Methods

* [captureStackTrace](executor.nopaymentaccounterror.md#capturestacktrace)
* [toString](executor.nopaymentaccounterror.md#tostring)

### Constructors

#### constructor

+ **new NoPaymentAccountError**\(`required_driver`: _any_, `required_network`: _any_\): [_NoPaymentAccountError_](executor.nopaymentaccounterror.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `required_driver` | _any_ |
| `required_network` | _any_ |

**Returns:** [_NoPaymentAccountError_](executor.nopaymentaccounterror.md)

Defined in: [yajsapi/executor/index.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L58)

### Properties

#### message

• **message**: _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:974

#### name

• **name**: _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:973

#### prepareStackTrace

• `Optional` **prepareStackTrace**: _undefined_ \| \(`err`: Error, `stackTraces`: CallSite\[\]\) =&gt; _any_

Optional override for formatting stack traces

**`see`** [https://github.com/v8/v8/wiki/Stack Trace API\#customizing-stack-traces](https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces)

Defined in: node\_modules/@types/node/globals.d.ts:11

#### required\_driver

• **required\_driver**: _string_

Defined in: [yajsapi/executor/index.ts:56](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L56)

#### required\_network

• **required\_network**: _string_

Defined in: [yajsapi/executor/index.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L58)

#### stack

• `Optional` **stack**: _undefined_ \| _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:975

#### stackTraceLimit

• **stackTraceLimit**: _number_

Defined in: node\_modules/@types/node/globals.d.ts:13

### Methods

#### captureStackTrace

▸ **captureStackTrace**\(`targetObject`: _object_, `constructorOpt?`: Function\): _void_

Create .stack property on a target object

**Parameters:**

| Name | Type |
| :--- | :--- |
| `targetObject` | _object_ |
| `constructorOpt?` | Function |

**Returns:** _void_

Defined in: node\_modules/@types/node/globals.d.ts:4

#### toString

▸ **toString**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/executor/index.ts:66](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/index.ts#L66)

