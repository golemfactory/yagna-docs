[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / TaskAccepted

# Class: TaskAccepted

[executor/events](../modules/executor_events.md).TaskAccepted

## Hierarchy

- `TaskEvent`

  ↳ **TaskAccepted**

## Table of contents

### Constructors

- [constructor](executor_events.taskaccepted.md#constructor)

### Properties

- [result](executor_events.taskaccepted.md#result)
- [task\_id](executor_events.taskaccepted.md#task_id)

### Methods

- [extract\_exc\_info](executor_events.taskaccepted.md#extract_exc_info)

## Constructors

### constructor

• **new TaskAccepted**(`__namedParameters`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `__namedParameters` | `Object` |

#### Overrides

TaskEvent.constructor

#### Defined in

[yajsapi/executor/events.ts:466](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L466)

## Properties

### result

• `Optional` **result**: `any`

#### Defined in

[yajsapi/executor/events.ts:466](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L466)

___

### task\_id

• `Optional` **task\_id**: `string`

#### Inherited from

TaskEvent.task\_id

#### Defined in

[yajsapi/executor/events.ts:244](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L244)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

Extract exception information from this event.

#### Returns

[`undefined` \| ``null`` \| `Error`, [YaEvent](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

#### Inherited from

TaskEvent.extract\_exc\_info

#### Defined in

[yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L17)
