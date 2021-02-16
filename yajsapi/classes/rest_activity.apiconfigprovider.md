# Class: ApiConfigProvider

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/activity](../modules/rest_activity.md) / ApiConfigProvider

## Class: ApiConfigProvider

[rest/activity](../modules/rest_activity.md).ApiConfigProvider

### Hierarchy

* _BaseAPI_

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

+ **new ApiConfigProvider**\(`api`: _BaseAPI_\): [_ApiConfigProvider_](rest_activity.apiconfigprovider.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `api` | _BaseAPI_ |

**Returns:** [_ApiConfigProvider_](rest_activity.apiconfigprovider.md)

Defined in: [yajsapi/rest/activity.ts:602](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L602)

### Properties

#### axios

• `Protected` **axios**: AxiosInstance

Defined in: node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:41

#### basePath

• `Protected` **basePath**: _string_

Defined in: node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:40

#### configuration

• `Protected` **configuration**: _undefined_ \| _Configuration_

Defined in: node\_modules/ya-ts-client/dist/ya-activity/base.d.ts:42

### Methods

#### api\_key

▸ **api\_key**\(\): _Promise_&lt;_undefined_ \| _string_&gt;

**Returns:** _Promise_&lt;_undefined_ \| _string_&gt;

Defined in: [yajsapi/rest/activity.ts:614](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L614)

#### base\_path

▸ **base\_path**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/activity.ts:608](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L608)

