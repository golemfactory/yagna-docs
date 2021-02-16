# Class: VmPackage

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [package](../modules/package.md) / VmPackage

## Class: VmPackage

[package](../modules/package.md).VmPackage

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

• **\_\_namedParameters**: _Object_

**Returns:** [_VmPackage_](package.vmpackage.md)

Inherited from: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:47](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L47)

### Properties

#### constraints

• **constraints**: [_Constraints_](package.constraints.md)

Defined in: [yajsapi/package/index.ts:46](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L46)

#### image\_hash

• **image\_hash**: _string_

Defined in: [yajsapi/package/index.ts:45](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L45)

#### repo\_url

• **repo\_url**: _string_

Defined in: [yajsapi/package/index.ts:44](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L44)

#### secure

• **secure**: _boolean_

Defined in: [yajsapi/package/index.ts:47](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L47)

### Methods

#### decorate\_demand

▸ **decorate\_demand**\(`demand`: [_DemandBuilder_](props_builder.demandbuilder.md)\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `demand` | [_DemandBuilder_](props_builder.demandbuilder.md) |

**Returns:** _Promise_&lt;_void_&gt;

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:68](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L68)

#### resolve\_url

▸ **resolve\_url**\(\): _Promise_&lt;_string_&gt;

**Returns:** _Promise_&lt;_string_&gt;

Overrides: [Package](package.package-1.md)

Defined in: [yajsapi/package/index.ts:57](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/package/index.ts#L57)

