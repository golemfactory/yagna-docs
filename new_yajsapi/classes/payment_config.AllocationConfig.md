# Class: AllocationConfig

[payment/config](../modules/payment_config.md).AllocationConfig

## Hierarchy

- `BaseConfig`

  ↳ **`AllocationConfig`**

## Table of contents

### Constructors

- [constructor](payment_config.AllocationConfig.md#constructor)

### Properties

- [budget](payment_config.AllocationConfig.md#budget)
- [payment](payment_config.AllocationConfig.md#payment)
- [expires](payment_config.AllocationConfig.md#expires)
- [account](payment_config.AllocationConfig.md#account)
- [yagnaOptions](payment_config.AllocationConfig.md#yagnaoptions)
- [paymentTimeout](payment_config.AllocationConfig.md#paymenttimeout)
- [api](payment_config.AllocationConfig.md#api)
- [logger](payment_config.AllocationConfig.md#logger)
- [eventTarget](payment_config.AllocationConfig.md#eventtarget)
- [paymentRequestTimeout](payment_config.AllocationConfig.md#paymentrequesttimeout)
- [options](payment_config.AllocationConfig.md#options)

## Constructors

### constructor

• **new AllocationConfig**(`options?`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `options?` | [`AllocationOptions`](../interfaces/payment_allocation.AllocationOptions.md) |

#### Overrides

BaseConfig.constructor

#### Defined in

[yajsapi/payment/config.ts:85](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L85)

## Properties

### budget

• `Readonly` **budget**: `number`

#### Defined in

[yajsapi/payment/config.ts:80](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L80)

___

### payment

• `Readonly` **payment**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `driver` | `string` |
| `network` | `string` |

#### Overrides

BaseConfig.payment

#### Defined in

[yajsapi/payment/config.ts:81](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L81)

___

### expires

• `Readonly` **expires**: `number`

#### Defined in

[yajsapi/payment/config.ts:82](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L82)

___

### account

• `Readonly` **account**: `Object`

#### Type declaration

| Name | Type |
| :------ | :------ |
| `address` | `string` |
| `platform` | `string` |

#### Defined in

[yajsapi/payment/config.ts:83](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L83)

___

### yagnaOptions

• `Optional` `Readonly` **yagnaOptions**: [`YagnaOptions`](../modules/executor_executor.md#yagnaoptions)

#### Inherited from

BaseConfig.yagnaOptions

#### Defined in

[yajsapi/payment/config.ts:36](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L36)

___

### paymentTimeout

• `Readonly` **paymentTimeout**: `number`

#### Inherited from

BaseConfig.paymentTimeout

#### Defined in

[yajsapi/payment/config.ts:37](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L37)

___

### api

• `Readonly` **api**: `RequestorApi`

#### Inherited from

BaseConfig.api

#### Defined in

[yajsapi/payment/config.ts:38](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L38)

___

### logger

• `Optional` `Readonly` **logger**: [`Logger`](../interfaces/utils_logger.Logger.md)

#### Inherited from

BaseConfig.logger

#### Defined in

[yajsapi/payment/config.ts:39](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L39)

___

### eventTarget

• `Optional` `Readonly` **eventTarget**: `EventTarget`

#### Inherited from

BaseConfig.eventTarget

#### Defined in

[yajsapi/payment/config.ts:40](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L40)

___

### paymentRequestTimeout

• `Readonly` **paymentRequestTimeout**: `number`

#### Inherited from

BaseConfig.paymentRequestTimeout

#### Defined in

[yajsapi/payment/config.ts:42](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L42)

___

### options

• `Optional` `Readonly` **options**: [`BasePaymentOptions`](../interfaces/payment_config.BasePaymentOptions.md)

#### Inherited from

BaseConfig.options

#### Defined in

[yajsapi/payment/config.ts:44](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/payment/config.ts#L44)
