[yajsapi](../README.md) / [Exports](../modules.md) / [executor](../modules/executor.md) / NoPaymentAccountError

# Class: NoPaymentAccountError

[executor](../modules/executor.md).NoPaymentAccountError

## Hierarchy

- `Error`

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

• **new NoPaymentAccountError**(`required_driver`, `required_network`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `required_driver` | `any` |
| `required_network` | `any` |

#### Overrides

Error.constructor

#### Defined in

[yajsapi/executor/index.ts:78](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L78)

## Properties

### message

• **message**: `string`

#### Inherited from

Error.message

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:974

___

### name

• **name**: `string`

#### Inherited from

Error.name

#### Defined in

node_modules/typescript/lib/lib.es5.d.ts:973

___

### required\_driver

• **required\_driver**: `string`

#### Defined in

[yajsapi/executor/index.ts:76](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L76)

___

### required\_network

• **required\_network**: `string`

#### Defined in

[yajsapi/executor/index.ts:78](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L78)

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

[yajsapi/executor/index.ts:86](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L86)

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
