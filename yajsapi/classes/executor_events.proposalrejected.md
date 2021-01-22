[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ProposalRejected

# Class: ProposalRejected

[executor/events](../modules/executor_events.md).ProposalRejected

## Hierarchy

* *ProposalEvent*

  ↳ **ProposalRejected**

## Table of contents

### Constructors

- [constructor](executor_events.proposalrejected.md#constructor)

### Properties

- [prop\_id](executor_events.proposalrejected.md#prop_id)
- [reason](executor_events.proposalrejected.md#reason)

### Methods

- [extract\_exc\_info](executor_events.proposalrejected.md#extract_exc_info)

## Constructors

### constructor

\+ **new ProposalRejected**(`__namedParameters`: *Object*): [*ProposalRejected*](executor_events.proposalrejected.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ProposalRejected*](executor_events.proposalrejected.md)

Defined in: [yajsapi/executor/events.ts:80](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L80)

## Properties

### prop\_id

• `Optional` **prop\_id**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L67)

___

### reason

• `Optional` **reason**: *undefined* \| *string*

Defined in: [yajsapi/executor/events.ts:80](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L80)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
