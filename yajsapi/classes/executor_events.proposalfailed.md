[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ProposalFailed

# Class: ProposalFailed

[executor/events](../modules/executor_events.md).ProposalFailed

## Hierarchy

* *ProposalEvent*

  ↳ **ProposalFailed**

## Table of contents

### Constructors

- [constructor](executor_events.proposalfailed.md#constructor)

### Properties

- [prop\_id](executor_events.proposalfailed.md#prop_id)
- [reason](executor_events.proposalfailed.md#reason)

### Methods

- [extract\_exc\_info](executor_events.proposalfailed.md#extract_exc_info)

## Constructors

### constructor

\+ **new ProposalFailed**(`__namedParameters`: *Object*): [*ProposalFailed*](executor_events.proposalfailed.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ProposalFailed*](executor_events.proposalfailed.md)

Defined in: [yajsapi/executor/events.ts:103](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L103)

## Properties

### prop\_id

• `Optional` **prop\_id**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L67)

___

### reason

• `Optional` **reason**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:103](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L103)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
