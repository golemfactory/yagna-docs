[yajsapi](../README.md) / [Exports](../modules.md) / [package](../modules/package.md) / VmPackage

# Class: VmPackage

[package](../modules/package.md).VmPackage

## Hierarchy

- [Package](package.package-1.md)

  ↳ **VmPackage**

## Table of contents

### Constructors

- [constructor](package.vmpackage.md#constructor)

### Properties

- [constraints](package.vmpackage.md#constraints)
- [image\_hash](package.vmpackage.md#image_hash)
- [repo\_url](package.vmpackage.md#repo_url)
- [secure](package.vmpackage.md#secure)

### Methods

- [decorate\_demand](package.vmpackage.md#decorate_demand)
- [resolve\_url](package.vmpackage.md#resolve_url)

## Constructors

### constructor

• **new VmPackage**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

[Package](package.package-1.md).[constructor](package.package-1.md#constructor)

#### Defined in

[yajsapi/package/index.ts:47](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L47)

## Properties

### constraints

• **constraints**: [Constraints](package.constraints.md)

#### Defined in

[yajsapi/package/index.ts:46](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L46)

___

### image\_hash

• **image\_hash**: `string`

#### Defined in

[yajsapi/package/index.ts:45](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L45)

___

### repo\_url

• **repo\_url**: `string`

#### Defined in

[yajsapi/package/index.ts:44](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L44)

___

### secure

• **secure**: `boolean`

#### Defined in

[yajsapi/package/index.ts:47](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L47)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`): `Promise`<void\>

#### Parameters

| Name | Type |
| :------ | :------ |
| `demand` | [DemandBuilder](props_builder.demandbuilder.md) |

#### Returns

`Promise`<void\>

#### Overrides

[Package](package.package-1.md).[decorate_demand](package.package-1.md#decorate_demand)

#### Defined in

[yajsapi/package/index.ts:68](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L68)

___

### resolve\_url

▸ **resolve_url**(): `Promise`<string\>

#### Returns

`Promise`<string\>

#### Overrides

[Package](package.package-1.md).[resolve_url](package.package-1.md#resolve_url)

#### Defined in

[yajsapi/package/index.ts:57](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L57)
