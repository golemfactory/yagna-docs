[yajsapi](../README.md) / [Exports](../modules.md) / [crypto](../modules/crypto.md) / CryptoCtx

# Class: CryptoCtx

[crypto](../modules/crypto.md).CryptoCtx

## Hierarchy

* **CryptoCtx**

## Table of contents

### Constructors

- [constructor](crypto.cryptoctx.md#constructor)

### Properties

- [ephem\_key](crypto.cryptoctx.md#ephem_key)
- [priv\_key](crypto.cryptoctx.md#priv_key)

### Methods

- [decrypt](crypto.cryptoctx.md#decrypt)
- [encrypt](crypto.cryptoctx.md#encrypt)
- [from](crypto.cryptoctx.md#from)

## Constructors

### constructor

\+ `Private`**new CryptoCtx**(`priv_key`: [*PrivateKey*](crypto.privatekey.md), `ephem_key`: *Buffer*): [*CryptoCtx*](crypto.cryptoctx.md)

#### Parameters:

Name | Type |
------ | ------ |
`priv_key` | [*PrivateKey*](crypto.privatekey.md) |
`ephem_key` | *Buffer* |

**Returns:** [*CryptoCtx*](crypto.cryptoctx.md)

Defined in: [yajsapi/crypto.ts:77](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L77)

## Properties

### ephem\_key

• **ephem\_key**: *Buffer*

Defined in: [yajsapi/crypto.ts:71](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L71)

___

### priv\_key

• **priv\_key**: [*PrivateKey*](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:70](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L70)

## Methods

### decrypt

▸ **decrypt**(`data`: *Buffer*): *Buffer*

#### Parameters:

Name | Type |
------ | ------ |
`data` | *Buffer* |

**Returns:** *Buffer*

Defined in: [yajsapi/crypto.ts:106](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L106)

___

### encrypt

▸ **encrypt**(`data`: *Buffer*): *Buffer*

#### Parameters:

Name | Type |
------ | ------ |
`data` | *Buffer* |

**Returns:** *Buffer*

Defined in: [yajsapi/crypto.ts:84](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L84)

___

### from

▸ `Static`**from**(`pub_key`: [*PublicKey*](crypto.publickey.md), `priv_key?`: [*PrivateKey*](crypto.privatekey.md)): *Promise*<[*CryptoCtx*](crypto.cryptoctx.md)\>

#### Parameters:

Name | Type |
------ | ------ |
`pub_key` | [*PublicKey*](crypto.publickey.md) |
`priv_key?` | [*PrivateKey*](crypto.privatekey.md) |

**Returns:** *Promise*<[*CryptoCtx*](crypto.cryptoctx.md)\>

Defined in: [yajsapi/crypto.ts:73](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L73)
