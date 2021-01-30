# executor/events/paymentaccepted

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / PaymentAccepted

## Class: PaymentAccepted

[executor/events](../yajsapi-2/executor_events.md).PaymentAccepted

### Hierarchy

* _AgreementEvent_

  ↳ **PaymentAccepted**

### Table of contents

#### Constructors

* [constructor](executor_events.paymentaccepted.md#constructor)

#### Properties

* [agr\_id](executor_events.paymentaccepted.md#agr_id)
* [amount](executor_events.paymentaccepted.md#amount)
* [inv\_id](executor_events.paymentaccepted.md#inv_id)

#### Methods

* [extract\_exc\_info](executor_events.paymentaccepted.md#extract_exc_info)

### Constructors

#### constructor

+ **new PaymentAccepted**\(`__namedParameters`: _Object_\): [_PaymentAccepted_](executor_events.paymentaccepted.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_PaymentAccepted_](executor_events.paymentaccepted.md)

Defined in: [yajsapi/executor/events.ts:158](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L158)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

#### amount

• **amount**: _string_

Defined in: [yajsapi/executor/events.ts:158](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L158)

#### inv\_id

• **inv\_id**: _string_

Defined in: [yajsapi/executor/events.ts:157](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L157)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)

