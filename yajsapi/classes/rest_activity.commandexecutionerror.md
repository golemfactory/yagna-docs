[yajsapi](../README.md) / [Exports](../modules.md) / [rest/activity](../modules/rest_activity.md) / CommandExecutionError

# Class: CommandExecutionError

[rest/activity](../modules/rest_activity.md).CommandExecutionError

## Hierarchy

* *Error*

  ↳ **CommandExecutionError**

## Table of contents

### Constructors

- [constructor](rest_activity.commandexecutionerror.md#constructor)

### Properties

- [command](rest_activity.commandexecutionerror.md#command)
- [message](rest_activity.commandexecutionerror.md#message)
- [name](rest_activity.commandexecutionerror.md#name)
- [prepareStackTrace](rest_activity.commandexecutionerror.md#preparestacktrace)
- [stack](rest_activity.commandexecutionerror.md#stack)
- [stackTraceLimit](rest_activity.commandexecutionerror.md#stacktracelimit)

### Methods

- [captureStackTrace](rest_activity.commandexecutionerror.md#capturestacktrace)
- [toString](rest_activity.commandexecutionerror.md#tostring)

## Constructors

### constructor

\+ **new CommandExecutionError**(`command`: *string*, `message?`: *string*): [*CommandExecutionError*](rest_activity.commandexecutionerror.md)

#### Parameters:

Name | Type |
------ | ------ |
`command` | *string* |
`message?` | *string* |

**Returns:** [*CommandExecutionError*](rest_activity.commandexecutionerror.md)

Defined in: [yajsapi/rest/activity.ts:342](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L342)

## Properties

### command

• **command**: *string*

Defined in: [yajsapi/rest/activity.ts:341](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L341)

___

### message

• **message**: *string*

Defined in: [yajsapi/rest/activity.ts:342](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L342)

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

Defined in: [yajsapi/rest/activity.ts:348](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L348)
