# Class: ActivityCreated

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ActivityCreated

## Class: ActivityCreated

[executor/events](../modules/executor_events.md).ActivityCreated

### Hierarchy

* _AgreementEvent_

  ↳ **ActivityCreated**

### Table of contents

#### Constructors

* [constructor](executor_events.activitycreated.md#constructor)

#### Properties

* [act\_id](executor_events.activitycreated.md#act_id)
* [agr\_id](executor_events.activitycreated.md#agr_id)

#### Methods

* [extract\_exc\_info](executor_events.activitycreated.md#extract_exc_info)

### Constructors

#### constructor

+ **new ActivityCreated**\(`__namedParameters`: _Object_\): [_ActivityCreated_](executor_events.activitycreated.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ActivityCreated_](executor_events.activitycreated.md)

Defined in: [yajsapi/executor/events.ts:226](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L226)

### Properties

#### act\_id

• `Optional` **act\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:226](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L226)

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

