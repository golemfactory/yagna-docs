# Class: CommandStdOut

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandStdOut

## Class: CommandStdOut

[executor/events](../modules/executor_events.md).CommandStdOut

### Hierarchy

* [_CommandEvent_](executor_events.commandevent.md)

  ↳ **CommandStdOut**

### Table of contents

#### Constructors

* [constructor](executor_events.commandstdout.md#constructor)

#### Properties

* [agr\_id](executor_events.commandstdout.md#agr_id)
* [cmd\_idx](executor_events.commandstdout.md#cmd_idx)
* [output](executor_events.commandstdout.md#output)
* [task\_id](executor_events.commandstdout.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandstdout.md#extract_exc_info)

### Constructors

#### constructor

* **new CommandStdOut**\(`__namedParameters`: _Object_\): [_CommandStdOut_](executor_events.commandstdout.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_CommandStdOut_](executor_events.commandstdout.md)

Inherited from: [CommandEvent](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:312](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L312)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Inherited from: [CommandEvent](executor_events.commandevent.md).[agr\_id](executor_events.commandevent.md#agr_id)

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### cmd\_idx

• **cmd\_idx**: _number_

Inherited from: [CommandEvent](executor_events.commandevent.md).[cmd\_idx](executor_events.commandevent.md#cmd_idx)

Defined in: [yajsapi/executor/events.ts:312](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L312)

#### output

• **output**: _string_

Defined in: [yajsapi/executor/events.ts:447](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L447)

#### task\_id

• `Optional` **task\_id**: _undefined_ \| _null_ \| _string_

Inherited from: [CommandEvent](executor_events.commandevent.md).[task\_id](executor_events.commandevent.md#task_id)

Defined in: [yajsapi/executor/events.ts:282](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L282)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Inherited from: [CommandEvent](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L17)

