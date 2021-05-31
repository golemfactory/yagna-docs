# Class: PaymentFailed

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / PaymentFailed

## Class: PaymentFailed

[executor/events](../modules/executor_events.md).PaymentFailed

### Hierarchy

* _AgreementEvent_

  ↳ **PaymentFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.paymentfailed.md#constructor)

#### Properties

* [agr\_id](executor_events.paymentfailed.md#agr_id)
* [reason](executor_events.paymentfailed.md#reason)

#### Methods

* [extract\_exc\_info](executor_events.paymentfailed.md#extract_exc_info)

### Constructors

#### constructor

* **new PaymentFailed**\(`__namedParameters`: _Object_\): [_PaymentFailed_](executor_events.paymentfailed.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_PaymentFailed_](executor_events.paymentfailed.md)

Defined in: [yajsapi/executor/events.ts:182](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L182)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### reason

• **reason**: _string_

Defined in: [yajsapi/executor/events.ts:182](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L182)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

