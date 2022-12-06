# Class: DemandEvent

[market/demand](../modules/market_demand.md).DemandEvent

## Hierarchy

- `Event`

  ↳ **`DemandEvent`**

## Table of contents

### Constructors

- [constructor](market_demand.DemandEvent.md#constructor)

### Properties

- [proposal](market_demand.DemandEvent.md#proposal)

## Constructors

### constructor

• **new DemandEvent**(`type`, `data`)

Create a new instance of DemandEvent

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `type` | `any` | A string with the name of the event: |
| `data` | `any` | object with proposal data: |

#### Overrides

Event.constructor

#### Defined in

[yajsapi/market/demand.ts:118](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L118)

## Properties

### proposal

• `Readonly` **proposal**: [`Proposal`](market_proposal.Proposal.md)

#### Defined in

[yajsapi/market/demand.ts:111](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/market/demand.ts#L111)