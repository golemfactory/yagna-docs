[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ProposalConfirmed

# Class: ProposalConfirmed

[executor/events](../modules/executor_events.md).ProposalConfirmed

## Hierarchy

* *ProposalEvent*

  ↳ **ProposalConfirmed**

## Table of contents

### Constructors

- [constructor](executor_events.proposalconfirmed.md#constructor)

### Properties

- [prop\_id](executor_events.proposalconfirmed.md#prop_id)

### Methods

- [extract\_exc\_info](executor_events.proposalconfirmed.md#extract_exc_info)

## Constructors

### constructor

\+ **new ProposalConfirmed**(`__namedParameters`: *Object*): [*ProposalConfirmed*](executor_events.proposalconfirmed.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ProposalConfirmed*](executor_events.proposalconfirmed.md)

Defined in: [yajsapi/executor/events.ts:95](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L95)

## Properties

### prop\_id

• `Optional` **prop\_id**: *undefined* \| *null* \| *string*

Defined in: [yajsapi/executor/events.ts:67](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L67)

## Methods

### extract\_exc\_info

▸ **extract_exc_info**(): [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

Extract exception information from this event.

**Returns:** [*undefined* \| *null* \| Error, [*YaEvent*](executor_events.yaevent.md)]

The extracted exception information and a copy of the event without the exception information.

Defined in: [yajsapi/executor/events.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L17)
