# Class: ComputationStarted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ComputationStarted

## Class: ComputationStarted

[executor/events](../modules/executor_events.md).ComputationStarted

### Hierarchy

* [_YaEvent_](executor_events.yaevent.md)

  ↳ **ComputationStarted**

### Table of contents

#### Constructors

* [constructor](executor_events.computationstarted.md#constructor)

#### Properties

* [expires](executor_events.computationstarted.md#expires)

#### Methods

* [extract\_exc\_info](executor_events.computationstarted.md#extract_exc_info)

### Constructors

#### constructor

* **new ComputationStarted**\(`__namedParameters`: _Object_\): [_ComputationStarted_](executor_events.computationstarted.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ComputationStarted_](executor_events.computationstarted.md)

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:23](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L23)

### Properties

#### expires

• `Optional` **expires**: _undefined_ \| _number_

Defined in: [yajsapi/executor/events.ts:23](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L23)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [YaEvent](executor_events.yaevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

