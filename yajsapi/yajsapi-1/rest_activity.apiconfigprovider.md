# rest/activity/apiconfigprovider

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/activity](../yajsapi-2/rest_activity.md) / ApiConfigProvider

## Class: ApiConfigProvider

[rest/activity](../yajsapi-2/rest_activity.md).ApiConfigProvider

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

Defined in: [yajsapi/rest/activity.ts:586](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L586)

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

Defined in: [yajsapi/rest/activity.ts:598](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L598)

#### base\_path

▸ **base\_path**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/rest/activity.ts:592](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L592)

