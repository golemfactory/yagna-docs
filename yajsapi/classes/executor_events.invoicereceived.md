[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / InvoiceReceived

# Class: InvoiceReceived

[executor/events](../modules/executor_events.md).InvoiceReceived

## Hierarchy

* *AgreementEvent*

  ↳ **InvoiceReceived**

## Table of contents

### Constructors

- [constructor](executor_events.invoicereceived.md#constructor)

### Properties

- [agr\_id](executor_events.invoicereceived.md#agr_id)
- [amount](executor_events.invoicereceived.md#amount)
- [inv\_id](executor_events.invoicereceived.md#inv_id)

### Methods

- [extract\_exc\_info](executor_events.invoicereceived.md#extract_exc_info)

## Constructors

### constructor

\+ **new InvoiceReceived**(`__namedParameters`: *Object*): [*InvoiceReceived*](executor_events.invoicereceived.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*InvoiceReceived*](executor_events.invoicereceived.md)

Defined in: [yajsapi/executor/events.ts:194](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L194)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

___

### amount

• `Optional` **amount**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:194](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L194)

___

### inv\_id

• `Optional` **inv\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:193](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L193)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
