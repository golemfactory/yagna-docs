[yajsapi](../README.md) / [Exports](../modules.md) / [utils/asyncExitStack](../modules/utils_asyncexitstack.md) / default

# Class: default

[utils/asyncExitStack](../modules/utils_asyncexitstack.md).default

## Table of contents

### Constructors

- [constructor](utils_asyncexitstack.default.md#constructor)

### Properties

- [\_stack](utils_asyncexitstack.default.md#_stack)

### Methods

- [aclose](utils_asyncexitstack.default.md#aclose)
- [enter\_async\_context](utils_asyncexitstack.default.md#enter_async_context)

## Constructors

### constructor

• **new default**()

## Properties

### \_stack

• `Private` **\_stack**: `any`[] = []

#### Defined in

[yajsapi/utils/asyncExitStack.ts:2](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/asyncExitStack.ts#L2)

## Methods

### aclose

▸ **aclose**(): `Promise`<void\>

#### Returns

`Promise`<void\>

#### Defined in

[yajsapi/utils/asyncExitStack.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/asyncExitStack.ts#L9)

___

### enter\_async\_context

▸ **enter_async_context**(`ctx`): `Promise`<any\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `ctx` | `any` |

#### Returns

`Promise`<any\>

#### Defined in

[yajsapi/utils/asyncExitStack.ts:3](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/utils/asyncExitStack.ts#L3)
