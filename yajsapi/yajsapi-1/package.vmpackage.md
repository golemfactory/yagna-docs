# package/vmpackage

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [package](../yajsapi-2/package.md) / VmPackage

## Class: VmPackage

[package](../yajsapi-2/package.md).VmPackage

### Hierarchy

* [_Package_](package.package-1.md)

  ↳ **VmPackage**

### Table of contents

#### Constructors

* [constructor](package.vmpackage.md#constructor)

#### Properties

* [constraints](package.vmpackage.md#constraints)
* [image\_hash](package.vmpackage.md#image_hash)
* [repo\_url](package.vmpackage.md#repo_url)
* [secure](package.vmpackage.md#secure)

#### Methods

* [decorate\_demand](package.vmpackage.md#decorate_demand)
* [resolve\_url](package.vmpackage.md#resolve_url)

### Constructors

#### constructor

+ **new VmPackage**\(`__namedParameters`: _Object_\): [_VmPackage_](package.vmpackage.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_VmPackage_](package.vmpackage.md)

Inherited from: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L43)

### Properties

#### constraints

• **constraints**: [_Constraints_](package.constraints.md)

Defined in: [yajsapi/package/index.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L42)

#### image\_hash

• **image\_hash**: _string_

Defined in: [yajsapi/package/index.ts:41](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L41)

#### repo\_url

• **repo\_url**: _string_

Defined in: [yajsapi/package/index.ts:40](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L40)

#### secure

• **secure**: _boolean_

Defined in: [yajsapi/package/index.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L43)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`: [_DemandBuilder_](props_builder.demandbuilder.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `demand` | [_DemandBuilder_](props_builder.demandbuilder.md) |

**Returns:** _Promise_&lt;_void_&gt;

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:64](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L64)

#### resolve\_url

▸ **resolve\_url**\(\): _Promise_&lt;_string_&gt;

**Returns:** _Promise_&lt;_string_&gt;

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:53](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/package/index.ts#L53)

