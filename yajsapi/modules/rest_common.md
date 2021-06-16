[yajsapi](../README.md) / [Exports](../modules.md) / rest/common

# Module: rest/common

## Table of contents

### Functions

- [is\_intermittent\_error](rest_common.md#is_intermittent_error)
- [repeat\_on\_error](rest_common.md#repeat_on_error)
- [suppress\_exceptions](rest_common.md#suppress_exceptions)

## Functions

### is\_intermittent\_error

▸ **is_intermittent_error**(`e`): `boolean`

#### Parameters

| Name | Type |
| :------ | :------ |
| `e` | `any` |

#### Returns

`boolean`

#### Defined in

[yajsapi/rest/common.ts:3](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/common.ts#L3)

___

### repeat\_on\_error

▸ **repeat_on_error**(`block`, `max_tries?`, `max_duration_ms?`, `interval_ms?`, `condition?`): `Promise`<any\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `block` | [default](../interfaces/utils_callable.default.md)<void, any\> | `undefined` |
| `max_tries` | `number` | 5 |
| `max_duration_ms` | `number` | 15000 |
| `interval_ms` | `number` | 1000 |
| `condition` | [default](../interfaces/utils_callable.default.md)<Error, boolean\> | `undefined` |

#### Returns

`Promise`<any\>

#### Defined in

[yajsapi/rest/common.ts:27](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/common.ts#L27)

___

### suppress\_exceptions

▸ **suppress_exceptions**(`condition`, `block`, `report_exceptions?`): `Promise`<any\>

#### Parameters

| Name | Type | Default value |
| :------ | :------ | :------ |
| `condition` | [default](../interfaces/utils_callable.default.md)<Error, boolean\> | `undefined` |
| `block` | [default](../interfaces/utils_callable.default.md)<void, any\> | `undefined` |
| `report_exceptions` | `boolean` | true |

#### Returns

`Promise`<any\>

#### Defined in

[yajsapi/rest/common.ts:11](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/rest/common.ts#L11)
