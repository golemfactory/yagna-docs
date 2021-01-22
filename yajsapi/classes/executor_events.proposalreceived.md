[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ProposalReceived

# Class: ProposalReceived

[executor/events](../modules/executor_events.md).ProposalReceived

## Hierarchy

* *ProposalEvent*

  ↳ **ProposalReceived**

## Table of contents

### Constructors

- [constructor](executor_events.proposalreceived.md#constructor)

### Properties

- [prop\_id](executor_events.proposalreceived.md#prop_id)
- [provider\_id](executor_events.proposalreceived.md#provider_id)

### Methods

- [extract\_exc\_info](executor_events.proposalreceived.md#extract_exc_info)

## Constructors

### constructor

\+ **new ProposalReceived**(`__namedParameters`: *Object*): [*ProposalReceived*](executor_events.proposalreceived.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ProposalReceived*](executor_events.proposalreceived.md)

Defined in: [yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L71)

## Properties

### prop\_id

• `Optional` **prop\_id**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L67)

___

### provider\_id

• `Optional` **provider\_id**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:71](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L71)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
