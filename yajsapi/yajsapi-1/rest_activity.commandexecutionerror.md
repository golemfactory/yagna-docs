# rest/activity/commandexecutionerror

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/activity](../yajsapi-2/rest_activity.md) / CommandExecutionError

## Class: CommandExecutionError

[rest/activity](../yajsapi-2/rest_activity.md).CommandExecutionError

### Hierarchy

* _Error_

  ↳ **CommandExecutionError**

### Table of contents

#### Constructors

* [constructor](rest_activity.commandexecutionerror.md#constructor)

#### Properties

* [command](rest_activity.commandexecutionerror.md#command)
* [message](rest_activity.commandexecutionerror.md#message)
* [name](rest_activity.commandexecutionerror.md#name)
* [prepareStackTrace](rest_activity.commandexecutionerror.md#preparestacktrace)
* [stack](rest_activity.commandexecutionerror.md#stack)
* [stackTraceLimit](rest_activity.commandexecutionerror.md#stacktracelimit)

#### Methods

* [captureStackTrace](rest_activity.commandexecutionerror.md#capturestacktrace)
* [toString](rest_activity.commandexecutionerror.md#tostring)

### Constructors

#### constructor

+ **new CommandExecutionError**\(`command`: _string_, `message?`: _string_\): [_CommandExecutionError_](rest_activity.commandexecutionerror.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `command` | _string_ |
| `message?` | _string_ |

**Returns:** [_CommandExecutionError_](rest_activity.commandexecutionerror.md)

Defined in: [yajsapi/rest/activity.ts:342](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L342)

### Properties

#### command

• **command**: _string_

Defined in: [yajsapi/rest/activity.ts:341](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L341)

#### message

• **message**: _string_

Defined in: [yajsapi/rest/activity.ts:342](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L342)

#### name

• **name**: _string_

Defined in: node\_modules/typescript/lib/lib.es5.d.ts:973

#### prepareStackTrace

• `Optional` **prepareStackTrace**: _undefined_ \| \(`err`: Error, `stackTraces`: CallSite\[\]\) =&gt; _any_

Optional override for formatting stack traces

**`see`** [https://github.com/v8/v8/wiki/Stack Trace API\#customizing-stack-traces](https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces)

Defined in: node\_modules/@types/node/globals.d.ts:11

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

Defined in: [yajsapi/rest/activity.ts:348](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L348)

