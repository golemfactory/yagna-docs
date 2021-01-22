[yajsapi](../README.md) / [Exports](../modules.md) / [package](../modules/package.md) / VmPackage

# Class: VmPackage

[package](../modules/package.md).VmPackage

## Hierarchy

* [*Package*](package.package-1.md)

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

\+ **new VmPackage**(`__namedParameters`: *Object*): [*VmPackage*](package.vmpackage.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*VmPackage*](package.vmpackage.md)

Inherited from: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L43)

## Properties

### constraints

• **constraints**: [*Constraints*](package.constraints.md)

Defined in: [yajsapi/package/index.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L42)

___

### image\_hash

• **image\_hash**: *string*

Defined in: [yajsapi/package/index.ts:41](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L41)

___

### repo\_url

• **repo\_url**: *string*

Defined in: [yajsapi/package/index.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L40)

___

### secure

• **secure**: *boolean*

Defined in: [yajsapi/package/index.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L43)

## Methods

### decorate\_demand

▸ **decorate_demand**(`demand`: [*DemandBuilder*](props_builder.demandbuilder.md)): *Promise*<*void*\>

#### Parameters:

Name | Type |
------ | ------ |
`demand` | [*DemandBuilder*](props_builder.demandbuilder.md) |

**Returns:** *Promise*<*void*\>

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:64](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L64)

___

### resolve\_url

▸ **resolve_url**(): *Promise*<*string*\>

**Returns:** *Promise*<*string*\>

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:53](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L53)
