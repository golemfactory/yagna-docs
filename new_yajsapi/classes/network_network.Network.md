# Class: Network

[network/network](../modules/network_network.md).Network

Network

**`Description`**

Describes a VPN created between the requestor and the provider nodes within Golem Network.

## Table of contents

### Methods

- [create](network_network.Network.md#create)
- [getNetworkInfo](network_network.Network.md#getnetworkinfo)
- [addNode](network_network.Network.md#addnode)
- [remove](network_network.Network.md#remove)

### Properties

- [id](network_network.Network.md#id)
- [config](network_network.Network.md#config)

## Methods

### create

▸ `Static` **create**(`options`): `Promise`<[`Network`](network_network.Network.md)\>

Create a new VPN.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `options` | [`NetworkOptions`](../interfaces/network_network.NetworkOptions.md) | [NetworkOptions](../interfaces/network_network.NetworkOptions.md) |

#### Returns

`Promise`<[`Network`](network_network.Network.md)\>

#### Defined in

[yajsapi/network/network.ts:57](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L57)

___

### getNetworkInfo

▸ **getNetworkInfo**(): [`NetworkInfo`](../interfaces/network_network.NetworkInfo.md)

Get Network Information

#### Returns

[`NetworkInfo`](../interfaces/network_network.NetworkInfo.md)

NetworkInfo

#### Defined in

[yajsapi/network/network.ts:102](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L102)

___

### addNode

▸ **addNode**(`nodeId`, `ip?`): `Promise`<[`NetworkNode`](network_node.NetworkNode.md)\>

Add a new node to the network.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `nodeId` | `string` | Node ID within the Golem network of this VPN node |
| `ip?` | `string` | IP address to assign to this node |

#### Returns

`Promise`<[`NetworkNode`](network_node.NetworkNode.md)\>

#### Defined in

[yajsapi/network/network.ts:117](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L117)

___

### remove

▸ **remove**(): `Promise`<`boolean`\>

Remove this network, terminating any connections it provides

#### Returns

`Promise`<`boolean`\>

#### Defined in

[yajsapi/network/network.ts:140](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L140)

## Properties

### id

• `Readonly` **id**: `string`

#### Defined in

[yajsapi/network/network.ts:87](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L87)

___

### config

• `Readonly` **config**: [`NetworkConfig`](network_config.NetworkConfig.md)

#### Defined in

[yajsapi/network/network.ts:87](https://github.com/golemfactory/yajsapi/blob/dec68b9/yajsapi/network/network.ts#L87)
