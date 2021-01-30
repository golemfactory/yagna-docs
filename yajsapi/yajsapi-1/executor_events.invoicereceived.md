# executor/events/invoicereceived

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / InvoiceReceived

## Class: InvoiceReceived

[executor/events](../yajsapi-2/executor_events.md).InvoiceReceived

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

+ **new InvoiceReceived**\(`__namedParameters`: _Object_\): [_InvoiceReceived_](executor_events.invoicereceived.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_InvoiceReceived_](executor_events.invoicereceived.md)

Defined in: [yajsapi/executor/events.ts:194](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L194)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

#### amount

• `Optional` **amount**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:194](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L194)

#### inv\_id

• `Optional` **inv\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:193](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L193)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)

