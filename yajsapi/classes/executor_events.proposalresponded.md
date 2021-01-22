[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / ProposalResponded

# Class: ProposalResponded

[executor/events](../modules/executor_events.md).ProposalResponded

## Hierarchy

* *ProposalEvent*

  ↳ **ProposalResponded**

## Table of contents

### Constructors

- [constructor](executor_events.proposalresponded.md#constructor)

### Properties

- [prop\_id](executor_events.proposalresponded.md#prop_id)

### Methods

- [extract\_exc\_info](executor_events.proposalresponded.md#extract_exc_info)

## Constructors

### constructor

\+ **new ProposalResponded**(`__namedParameters`: *Object*): [*ProposalResponded*](executor_events.proposalresponded.md)

#### Parameters:

Name | Type |
------ | ------ |
`__namedParameters` | *Object* |

**Returns:** [*ProposalResponded*](executor_events.proposalresponded.md)

Defined in: [yajsapi/executor/events.ts:88](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/executor/events.ts#L88)

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
