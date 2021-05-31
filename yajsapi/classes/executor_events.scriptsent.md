# Class: ScriptSent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / ScriptSent

## Class: ScriptSent

[executor/events](../modules/executor_events.md).ScriptSent

### Hierarchy

* _ScriptEvent_

  ↳ **ScriptSent**

### Table of contents

#### Constructors

* [constructor](executor_events.scriptsent.md#constructor)

#### Properties

* [agr\_id](executor_events.scriptsent.md#agr_id)
* [cmds](executor_events.scriptsent.md#cmds)
* [task\_id](executor_events.scriptsent.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.scriptsent.md#extract_exc_info)

### Constructors

#### constructor

* **new ScriptSent**\(`__namedParameters`: _Object_\): [_ScriptSent_](executor_events.scriptsent.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_ScriptSent_](executor_events.scriptsent.md)

Defined in: [yajsapi/executor/events.ts:286](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L286)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### cmds

• `Optional` **cmds**: _any_

Defined in: [yajsapi/executor/events.ts:286](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L286)

#### task\_id

• `Optional` **task\_id**: _undefined_ \| _null_ \| _string_

Defined in: [yajsapi/executor/events.ts:282](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L282)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

