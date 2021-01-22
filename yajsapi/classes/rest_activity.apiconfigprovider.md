[yajsapi](../README.md) / [Exports](../modules.md) / [rest/activity](../modules/rest_activity.md) / ApiConfigProvider

# Class: ApiConfigProvider

[rest/activity](../modules/rest_activity.md).ApiConfigProvider

## Hierarchy

* *BaseAPI*

  ↳ **ApiConfigProvider**

## Table of contents

### Constructors

- [constructor](rest_activity.apiconfigprovider.md#constructor)

### Properties

- [axios](rest_activity.apiconfigprovider.md#axios)
- [basePath](rest_activity.apiconfigprovider.md#basepath)
- [configuration](rest_activity.apiconfigprovider.md#configuration)

### Methods

- [api\_key](rest_activity.apiconfigprovider.md#api_key)
- [base\_path](rest_activity.apiconfigprovider.md#base_path)

## Constructors

### constructor

\+ **new ApiConfigProvider**(`api`: *BaseAPI*): [*ApiConfigProvider*](rest_activity.apiconfigprovider.md)

#### Parameters:

Name | Type |
------ | ------ |
`api` | *BaseAPI* |

**Returns:** [*ApiConfigProvider*](rest_activity.apiconfigprovider.md)

Defined in: [yajsapi/rest/activity.ts:586](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L586)

## Properties

### axios

• `Protected` **axios**: AxiosInstance

Defined in: node_modules/ya-ts-client/dist/ya-activity/base.d.ts:41

___

### basePath

• `Protected` **basePath**: *string*

Defined in: node_modules/ya-ts-client/dist/ya-activity/base.d.ts:40

___

### configuration

• `Protected` **configuration**: *undefined* \| *Configuration*

Defined in: node_modules/ya-ts-client/dist/ya-activity/base.d.ts:42

## Methods

### api\_key

▸ **api_key**(): *Promise*<*undefined* \| *string*\>

**Returns:** *Promise*<*undefined* \| *string*\>

Defined in: [yajsapi/rest/activity.ts:598](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L598)

___

### base\_path

▸ **base_path**(): *string*

**Returns:** *string*

Defined in: [yajsapi/rest/activity.ts:592](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L592)
