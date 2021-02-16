# Class: DebitNoteReceived

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / DebitNoteReceived

## Class: DebitNoteReceived

[executor/events](../modules/executor_events.md).DebitNoteReceived

### Hierarchy

* _AgreementEvent_

  ↳ **DebitNoteReceived**

### Table of contents

#### Constructors

* [constructor](executor_events.debitnotereceived.md#constructor)

#### Properties

* [agr\_id](executor_events.debitnotereceived.md#agr_id)
* [amount](executor_events.debitnotereceived.md#amount)
* [note\_id](executor_events.debitnotereceived.md#note_id)

#### Methods

* [extract\_exc\_info](executor_events.debitnotereceived.md#extract_exc_info)

### Constructors

#### constructor

+ **new DebitNoteReceived**\(`__namedParameters`: _Object_\): [_DebitNoteReceived_](executor_events.debitnotereceived.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_DebitNoteReceived_](executor_events.debitnotereceived.md)

Defined in: [yajsapi/executor/events.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L160)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### amount

• **amount**: _string_

Defined in: [yajsapi/executor/events.ts:160](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L160)

#### note\_id

• **note\_id**: _string_

Defined in: [yajsapi/executor/events.ts:159](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L159)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

