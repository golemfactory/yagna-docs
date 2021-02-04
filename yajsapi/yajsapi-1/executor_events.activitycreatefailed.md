# executor/events/activitycreatefailed

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [executor/events](../yajsapi-2/executor_events.md) / ActivityCreateFailed

## Class: ActivityCreateFailed

[executor/events](../yajsapi-2/executor_events.md).ActivityCreateFailed

### Hierarchy

* _AgreementEvent_

  ↳ **ActivityCreateFailed**

### Table of contents

#### Constructors

* [constructor](executor_events.activitycreatefailed.md#constructor)

#### Properties

* [agr\_id](executor_events.activitycreatefailed.md#agr_id)

#### Methods

* [extract\_exc\_info](executor_events.activitycreatefailed.md#extract_exc_info)

### Constructors

#### constructor

+ **new ActivityCreateFailed**\(`__namedParameters`: _Object_\): [_ActivityCreateFailed_](executor_events.activitycreatefailed.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `__namedParameters` | _Object_ |

**Returns:** [_ActivityCreateFailed_](executor_events.activitycreatefailed.md)

Defined in: [yajsapi/executor/events.ts:219](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L219)

### Properties

#### agr\_id

• `Optional` **agr\_id**: _undefined_ \| _string_

Defined in: [yajsapi/executor/events.ts:123](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L123)

### Methods

#### extract\_exc\_info

▸ **extract\_exc\_info**\(\): \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

Extract exception information from this event.

**Returns:** \[_undefined_ \| _null_ \| Error, [_YaEvent_](executor_events.yaevent.md)\]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
