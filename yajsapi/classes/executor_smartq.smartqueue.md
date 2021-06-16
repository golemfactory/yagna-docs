# Class: SmartQueue

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor/smartq](../modules/executor_smartq.md) / SmartQueue

## Class: SmartQueue

[executor/smartq](../modules/executor_smartq.md).SmartQueue

### Type parameters

| Name |
| :--- |
| `Item` |

### Table of contents

#### Constructors

* [constructor](executor_smartq.smartqueue.md#constructor)

#### Properties

* [\_\_done](executor_smartq.smartqueue.md#__done)
* [\_\_eof](executor_smartq.smartqueue.md#__eof)
* [\_\_new\_items](executor_smartq.smartqueue.md#__new_items)
* [\_in\_progress](executor_smartq.smartqueue.md#_in_progress)
* [\_items](executor_smartq.smartqueue.md#_items)
* [\_rescheduled\_items](executor_smartq.smartqueue.md#_rescheduled_items)

#### Methods

* [\_\_find\_rescheduled\_item](executor_smartq.smartqueue.md#__find_rescheduled_item)
* [\_\_have\_data](executor_smartq.smartqueue.md#__have_data)
* [close](executor_smartq.smartqueue.md#close)
* [get](executor_smartq.smartqueue.md#get)
* [has\_unassigned\_items](executor_smartq.smartqueue.md#has_unassigned_items)
* [mark\_done](executor_smartq.smartqueue.md#mark_done)
* [new\_consumer](executor_smartq.smartqueue.md#new_consumer)
* [reschedule](executor_smartq.smartqueue.md#reschedule)
* [reschedule\_all](executor_smartq.smartqueue.md#reschedule_all)
* [stats](executor_smartq.smartqueue.md#stats)
* [wait\_until\_done](executor_smartq.smartqueue.md#wait_until_done)

### Constructors

#### constructor

• **new SmartQueue**\(`items`, `retry_cnt?`, ...`rest`\)

**Type parameters**

| Name |
| :--- |
| `Item` |

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `items` | `Item`\[\] | `undefined` |
| `retry_cnt` | `number` | 2 |
| `...rest` | `any`\[\] | `undefined` |

**Defined in**

[yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L38)

### Properties

#### \_\_done

• `Private` **\_\_done**: `any`

**Defined in**

[yajsapi/executor/smartq.ts:38](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L38)

#### \_\_eof

• `Private` **\_\_eof**: `any`

**Defined in**

[yajsapi/executor/smartq.ts:37](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L37)

#### \_\_new\_items

• `Private` **\_\_new\_items**: `any`

**Defined in**

[yajsapi/executor/smartq.ts:36](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L36)

#### \_in\_progress

• `Private` **\_in\_progress**: `Set`&lt;[Handle](executor_smartq.handle.md)&gt;

**Defined in**

[yajsapi/executor/smartq.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L35)

#### \_items

• `Private` **\_items**: `null` \| `Item`\[\]

**Defined in**

[yajsapi/executor/smartq.ts:33](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L33)

#### \_rescheduled\_items

• `Private` **\_rescheduled\_items**: `Set`&lt;[Handle](executor_smartq.handle.md)&gt;

**Defined in**

[yajsapi/executor/smartq.ts:34](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L34)

### Methods

#### \_\_find\_rescheduled\_item

▸ **\_\_find\_rescheduled\_item**\(`consumer`\): `null` \| [Handle](executor_smartq.handle.md)

**Parameters**

| Name | Type |
| :--- | :--- |
| `consumer` | [Consumer](executor_smartq.consumer.md) |

**Returns**

`null` \| [Handle](executor_smartq.handle.md)

**Defined in**

[yajsapi/executor/smartq.ts:73](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L73)

#### \_\_have\_data

▸ **\_\_have\_data**\(\): `boolean`

**Returns**

`boolean`

**Defined in**

[yajsapi/executor/smartq.ts:65](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L65)

#### close

▸ **close**\(\): `void`

**Returns**

`void`

**Defined in**

[yajsapi/executor/smartq.ts:50](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L50)

#### get

▸ **get**\(`consumer`, `callback`\): `AsyncGenerator`&lt;[Handle](executor_smartq.handle.md), any, unknown&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `consumer` | [Consumer](executor_smartq.consumer.md) |
| `callback` | `undefined` \| `null` \| `Function` |

**Returns**

`AsyncGenerator`&lt;[Handle](executor_smartq.handle.md), any, unknown&gt;

**Defined in**

[yajsapi/executor/smartq.ts:80](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L80)

#### has\_unassigned\_items

▸ **has\_unassigned\_items**\(\): `boolean`

**Returns**

`boolean`

**Defined in**

[yajsapi/executor/smartq.ts:162](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L162)

#### mark\_done

▸ **mark\_done**\(`handle`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `handle` | [Handle](executor_smartq.handle.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/smartq.ts:114](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L114)

#### new\_consumer

▸ **new\_consumer**\(\): [Consumer](executor_smartq.consumer.md)

**Returns**

[Consumer](executor_smartq.consumer.md)

**Defined in**

[yajsapi/executor/smartq.ts:61](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L61)

#### reschedule

▸ **reschedule**\(`handle`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `handle` | [Handle](executor_smartq.handle.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/smartq.ts:126](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L126)

#### reschedule\_all

▸ **reschedule\_all**\(`consumer`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `consumer` | [Consumer](executor_smartq.consumer.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/smartq.ts:134](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L134)

#### stats

▸ **stats**\(\): `object`

**Returns**

`object`

**Defined in**

[yajsapi/executor/smartq.ts:148](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L148)

#### wait\_until\_done

▸ **wait\_until\_done**\(\): `Promise`

**Returns**

`Promise`

**Defined in**

[yajsapi/executor/smartq.ts:156](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/smartq.ts#L156)

