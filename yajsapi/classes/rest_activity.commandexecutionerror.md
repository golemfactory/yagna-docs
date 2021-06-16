[yajsapi](../README.md) / [Exports](../modules.md) / [rest/activity](../modules/rest_activity.md) / CommandExecutionError

# Class: CommandExecutionError

[rest/activity](../modules/rest_activity.md).CommandExecutionError

## Hierarchy

- `Error`

  ↳ **CommandExecutionError**

## Table of contents

### Constructors

- [constructor](rest_activity.commandexecutionerror.md#constructor)

### Properties

- [command](rest_activity.commandexecutionerror.md#command)
- [message](rest_activity.commandexecutionerror.md#message)
- [name](rest_activity.commandexecutionerror.md#name)
- [stack](rest_activity.commandexecutionerror.md#stack)
- [prepareStackTrace](rest_activity.commandexecutionerror.md#preparestacktrace)
- [stackTraceLimit](rest_activity.commandexecutionerror.md#stacktracelimit)

### Methods

- [toString](rest_activity.commandexecutionerror.md#tostring)
- [captureStackTrace](rest_activity.commandexecutionerror.md#capturestacktrace)

## Constructors

### constructor

• **new CommandExecutionError**(`command`, `message?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `command` | `string` |
| `message?` | `string` |

#### Overrides

Error.constructor

#### Defined in

[yajsapi/rest/activity.ts:355](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L355)

## Properties

### command

• **command**: `string`

#### Defined in

[yajsapi/rest/activity.ts:354](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L354)

___

### message

• **message**: `string`

#### Overrides

Error.message

#### Defined in

[yajsapi/rest/activity.ts:355](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L355)

___

### name

• **name**: `string`

#### Inherited from

Error.name

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:973

___

### stack

• `Optional` **stack**: `string`

#### Inherited from

Error.stack

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:975

___

### prepareStackTrace

▪ `Static` `Optional` **prepareStackTrace**: (`err`: `Error`, `stackTraces`: `CallSite`[]) => `any`

Optional override for formatting stack traces

**`see`** https://github.com/v8/v8/wiki/Stack%20Trace%20API#customizing-stack-traces

#### Type declaration

▸ (`err`, `stackTraces`): `any`

##### Parameters

| Name | Type |
| :------ | :------ |
| `err` | `Error` |
| `stackTraces` | `CallSite`[] |

##### Returns

`any`

#### Inherited from

Error.prepareStackTrace

#### Defined in

node_modules/@types/node/globals.d.ts:11

___

### stackTraceLimit

▪ `Static` **stackTraceLimit**: `number`

#### Inherited from

Error.stackTraceLimit

#### Defined in

node_modules/@types/node/globals.d.ts:13

## Methods

### toString

▸ **toString**(): `string`

#### Returns

`string`

#### Defined in

[yajsapi/rest/activity.ts:361](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L361)

___

### captureStackTrace

▸ `Static` **captureStackTrace**(`targetObject`, `constructorOpt?`): `void`

Create .stack property on a target object

#### Parameters

| Name | Type |
| :------ | :------ |
| `targetObject` | `object` |
| `constructorOpt?` | `Function` |

#### Returns

`void`

#### Inherited from

Error.captureStackTrace

#### Defined in

node_modules/@types/node/globals.d.ts:4
