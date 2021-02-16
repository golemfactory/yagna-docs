# Class: CommandEvent

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandEvent

## Class: CommandEvent

[executor/events](../modules/executor_events.md).CommandEvent

### Hierarchy

* _ScriptEvent_

  ↳ **CommandEvent**

  ↳↳ [_CommandExecuted_](executor_events.commandexecuted.md)

  ↳↳ [_CommandStarted_](executor_events.commandstarted.md)

  ↳↳ [_CommandStdOut_](executor_events.commandstdout.md)

  ↳↳ [_CommandStdErr_](executor_events.commandstderr.md)

### Table of contents

#### Constructors

* [constructor](executor_events.commandevent.md#constructor)

#### Properties

* [agr\_id](executor_events.commandevent.md#agr_id)
* [cmd\_idx](executor_events.commandevent.md#cmd_idx)
* [task\_id](executor_events.commandevent.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandevent.md#extract_exc_info)

### Constructors

#### constructor

+ **new CommandEvent**\(`__namedParameters`: _Object_\): [_CommandEvent_](executor_events.commandevent.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_CommandEvent_](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:312](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L312)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### cmd\_idx

• **cmd\_idx**: _number_

Defined in: [yajsapi/executor/events.ts:312](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L312)

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

