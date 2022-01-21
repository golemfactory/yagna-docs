# Class: ApiConfigProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/activity](../modules/rest_activity.md) / ApiConfigProvider

## Class: ApiConfigProvider

[rest/activity](../modules/rest_activity.md).ApiConfigProvider

### Hierarchy

* `BaseAPI`

  ↳ **ApiConfigProvider**

### Table of contents

#### Constructors

* [constructor](rest_activity.apiconfigprovider.md#constructor)

#### Properties

* [axios](rest_activity.apiconfigprovider.md#axios)
* [basePath](rest_activity.apiconfigprovider.md#basepath)
* [configuration](rest_activity.apiconfigprovider.md#configuration)

#### Methods

* [api\_key](rest_activity.apiconfigprovider.md#api_key)
* [base\_path](rest_activity.apiconfigprovider.md#base_path)

### Constructors

#### constructor

• **new ApiConfigProvider**\(`api`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `api` | `BaseAPI` |

**Overrides**

BaseAPI.constructor

**Defined in**

[yajsapi/rest/activity.ts:618](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L618)

### Properties

#### axios

• `Protected` **axios**: `AxiosInstance`

**Inherited from**

BaseAPI.axios

**Defined in**

node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:41

#### basePath

• `Protected` **basePath**: `string`

**Inherited from**

BaseAPI.basePath

**Defined in**

node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:40

#### configuration

• `Protected` **configuration**: `undefined` \| `Configuration`

**Inherited from**

BaseAPI.configuration

**Defined in**

node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:42

### Methods

#### api\_key

▸ **api\_key**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/rest/activity.ts:630](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L630)

#### base\_path

▸ **base\_path**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/rest/activity.ts:624](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/activity.ts#L624)

