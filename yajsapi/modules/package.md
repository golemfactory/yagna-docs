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

Ƭ **RepoOpts**: { `engine?`: _string_ ; `image_hash`: _string_ ; `min_mem_gib`: _number_ ; `min_storage_gib`: _number_ }

**Type declaration:**

| Name | Type |
| :--- | :--- |
| `engine?` | _string_ |
| `image_hash` | _string_ |
| `min_mem_gib` | _number_ |
| `min_storage_gib` | _number_ |

Defined in: [yajsapi/package/index.ts:11](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L11)

### Variables

#### DEFAULT\_REPO\_SRV

• `Const` **DEFAULT\_REPO\_SRV**: _\_girepo.\_tcp.dev.golem.network_= "\_girepo.\_tcp.dev.golem.network"

Defined in: [yajsapi/package/index.ts:9](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L9)

### Functions

#### resolve\_repo\_srv

▸ `Const`**resolve\_repo\_srv**\(`__namedParameters`: _Object_\): _Promise_&lt;_unknown_&gt;

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** _Promise_&lt;_unknown_&gt;

Defined in: [yajsapi/package/index.ts:75](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L75)

