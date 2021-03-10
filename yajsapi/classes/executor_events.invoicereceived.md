# Class: InvoiceReceived

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / InvoiceReceived

## Class: InvoiceReceived

[executor/events](../modules/executor_events.md).InvoiceReceived

### Hierarchy

* _AgreementEvent_

  ↳ **InvoiceReceived**

### Table of contents

#### Constructors

* [constructor](executor_events.invoicereceived.md#constructor)

#### Properties

* [agr\_id](executor_events.invoicereceived.md#agr_id)
* [amount](executor_events.invoicereceived.md#amount)
* [inv\_id](executor_events.invoicereceived.md#inv_id)

#### Methods

* [extract\_exc\_info](executor_events.invoicereceived.md#extract_exc_info)

### Constructors

#### constructor

* **new InvoiceReceived**\(`__namedParameters`: _Object_\): [_InvoiceReceived_](executor_events.invoicereceived.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_InvoiceReceived_](executor_events.invoicereceived.md)

Defined in: [yajsapi/executor/events.ts:209](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L209)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### amount

• `Optional` **amount**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:209](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L209)

#### inv\_id

• `Optional` **inv\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:208](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L208)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

