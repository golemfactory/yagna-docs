[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / DebitNoteReceived

# Class: DebitNoteReceived

[executor/events](../modules/executor_events.md).DebitNoteReceived

## Hierarchy

* *AgreementEvent*

  ↳ **DebitNoteReceived**

## Table of contents

### Constructors

- [constructor](executor_events.debitnotereceived.md#constructor)

### Properties

- [agr\_id](executor_events.debitnotereceived.md#agr_id)
- [amount](executor_events.debitnotereceived.md#amount)
- [note\_id](executor_events.debitnotereceived.md#note_id)

### Methods

- [extract\_exc\_info](executor_events.debitnotereceived.md#extract_exc_info)

## Constructors

### constructor

\+ **new DebitNoteReceived**(`__namedParameters`: *Object*): [*DebitNoteReceived*](executor_events.debitnotereceived.md)

#### Parameters:

• **__namedParameters**: *Object*

**Returns:** [*DebitNoteReceived*](executor_events.debitnotereceived.md)

Defined in: [yajsapi/executor/events.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L160)

## Properties

### agr\_id

• `Optional` **agr\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

___

### amount

• **amount**: *string*

Defined in: [yajsapi/executor/events.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L160)

___

### note\_id

• **note\_id**: *string*

Defined in: [yajsapi/executor/events.ts:159](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L159)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)
