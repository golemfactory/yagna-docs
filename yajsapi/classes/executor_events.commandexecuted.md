# Class: CommandExecuted

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/events](../modules/executor_events.md) / CommandExecuted

## Class: CommandExecuted

[executor/events](../modules/executor_events.md).CommandExecuted

### Hierarchy

* [_CommandEvent_](executor_events.commandevent.md)

  ↳ **CommandExecuted**

### Table of contents

#### Constructors

* [constructor](executor_events.commandexecuted.md#constructor)

#### Properties

* [agr\_id](executor_events.commandexecuted.md#agr_id)
* [cmd\_idx](executor_events.commandexecuted.md#cmd_idx)
* [command](executor_events.commandexecuted.md#command)
* [message](executor_events.commandexecuted.md#message)
* [success](executor_events.commandexecuted.md#success)
* [task\_id](executor_events.commandexecuted.md#task_id)

#### Methods

* [extract\_exc\_info](executor_events.commandexecuted.md#extract_exc_info)

### Constructors

#### constructor

+ **new CommandExecuted**\(`__namedParameters`: _Object_\): [_CommandExecuted_](executor_events.commandexecuted.md)

**Parameters:**

• **\_\_namedParameters**: _Object_

**Returns:** [_CommandExecuted_](executor_events.commandexecuted.md)

Inherited from: [CommandEvent](executor_events.commandevent.md)

Defined in: [yajsapi/executor/events.ts:324](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L324)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Inherited from: [CommandEvent](executor_events.commandevent.md).[agr\_id](executor_events.commandevent.md#agr_id)

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L123)

#### cmd\_idx

• **cmd\_idx**: _number_

Inherited from: [CommandEvent](executor_events.commandevent.md).[cmd\_idx](executor_events.commandevent.md#cmd_idx)

Defined in: [yajsapi/executor/events.ts:312](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L312)

#### command

• `Optional` **command**: _any_

Defined in: [yajsapi/executor/events.ts:322](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L322)

#### message

• `Optional` **message**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:324](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L324)

#### success

• `Optional` **success**: _undefined_ \| _boolean_

Defined in: [yajsapi/executor/events.ts:323](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/executor/events.ts#L323)

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

