[yajsapi](../README.md) / [Exports](../modules.md) / [executor/events](../modules/executor_events.md) / CommandEventContext

# Class: CommandEventContext

[executor/events](../modules/executor_events.md).CommandEventContext

## Table of contents

### Constructors

- [constructor](executor_events.commandeventcontext.md#constructor)

### Properties

- [evt](executor_events.commandeventcontext.md#evt)

### Methods

- [computation\_finished](executor_events.commandeventcontext.md#computation_finished)
- [event](executor_events.commandeventcontext.md#event)
- [fromJson](executor_events.commandeventcontext.md#fromjson)

## Constructors

### constructor

• **new CommandEventContext**(`evt_cls`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `evt_cls` | `any` |

#### Defined in

[yajsapi/executor/events.ts:341](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L341)

## Properties

### evt

• **evt**: [CommandEvent](executor_events.commandevent.md)

#### Defined in

[yajsapi/executor/events.ts:341](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L341)

## Methods

### computation\_finished

▸ **computation_finished**(`last_idx`): `boolean`

#### Parameters

| Name | Type |
| :------ | :------ |
| `last_idx` | `any` |

#### Returns

`boolean`

#### Defined in

[yajsapi/executor/events.ts:395](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L395)

___

### event

▸ **event**(`agr_id`, `task_id`, `cmds`): [CommandEvent](executor_events.commandevent.md)

#### Parameters

| Name | Type |
| :------ | :------ |
| `agr_id` | `string` |
| `task_id` | `string` |
| `cmds` | `any`[] |

#### Returns

[CommandEvent](executor_events.commandevent.md)

#### Defined in

[yajsapi/executor/events.ts:405](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L405)

___

### fromJson

▸ `Static` **fromJson**(`json`): [CommandEventContext](executor_events.commandeventcontext.md)

#### Parameters

| Name | Type |
| :------ | :------ |
| `json` | `string` |

#### Returns

[CommandEventContext](executor_events.commandeventcontext.md)

#### Defined in

[yajsapi/executor/events.ts:346](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/events.ts#L346)
