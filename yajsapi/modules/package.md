# Module: package

[yajsapi](../yajsapi.md) / [Exports](./) / package

## Module: package

### Table of contents

#### Classes

* [Constraints](../classes/package.constraints.md)
* [Package](../classes/package.package-1.md)
* [VmPackage](../classes/package.vmpackage.md)

#### Type aliases

* [RepoOpts](package.md#repoopts)

#### Variables

* [DEFAULT\_REPO\_SRV](package.md#default_repo_srv)

#### Functions

* [resolve\_repo\_srv](package.md#resolve_repo_srv)

### Type aliases

#### RepoOpts

Ƭ **RepoOpts**: `Object`

**Type declaration**

| Name | Type |
| :--- | :--- |
| `engine?` | `string` |
| `image_hash` | `string` |
| `min_mem_gib` | `number` |
| `min_storage_gib` | `number` |

**Defined in**

[yajsapi/package/index.ts:11](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L11)

### Variables

#### DEFAULT\_REPO\_SRV

• `Const` **DEFAULT\_REPO\_SRV**: `"_girepo._tcp.dev.golem.network"`

**Defined in**

[yajsapi/package/index.ts:9](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L9)

### Functions

#### resolve\_repo\_srv

▸ `Const` **resolve\_repo\_srv**\(`__namedParameters`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | `Object` |

**Returns**

`Promise`

**Defined in**

[yajsapi/package/index.ts:75](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/package/index.ts#L75)

