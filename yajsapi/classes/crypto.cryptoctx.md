# Class: CryptoCtx

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [crypto](../modules/crypto.md) / CryptoCtx

## Class: CryptoCtx

[crypto](../modules/crypto.md).CryptoCtx

### Table of contents

#### Constructors

* [constructor](crypto.cryptoctx.md#constructor)

#### Properties

* [ephem\_key](crypto.cryptoctx.md#ephem_key)
* [priv\_key](crypto.cryptoctx.md#priv_key)

#### Methods

* [decrypt](crypto.cryptoctx.md#decrypt)
* [encrypt](crypto.cryptoctx.md#encrypt)
* [from](crypto.cryptoctx.md#from)

### Constructors

#### constructor

• `Private` **new CryptoCtx**\(`priv_key`, `ephem_key`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `priv_key` | [PrivateKey](crypto.privatekey.md) |
| `ephem_key` | `Buffer` |

**Defined in**

[yajsapi/crypto.ts:77](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L77)

### Properties

#### ephem\_key

• **ephem\_key**: `Buffer`

**Defined in**

[yajsapi/crypto.ts:71](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L71)

#### priv\_key

• **priv\_key**: [PrivateKey](crypto.privatekey.md)

**Defined in**

[yajsapi/crypto.ts:70](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L70)

### Methods

#### decrypt

▸ **decrypt**\(`data`\): `Buffer`

**Parameters**

| Name | Type |
| :--- | :--- |
| `data` | `Buffer` |

**Returns**

`Buffer`

**Defined in**

[yajsapi/crypto.ts:106](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L106)

#### encrypt

▸ **encrypt**\(`data`\): `Buffer`

**Parameters**

| Name | Type |
| :--- | :--- |
| `data` | `Buffer` |

**Returns**

`Buffer`

**Defined in**

[yajsapi/crypto.ts:84](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L84)

#### from

▸ `Static` **from**\(`pub_key`, `priv_key?`\): `Promise`&lt;[CryptoCtx](crypto.cryptoctx.md)&gt;

**Parameters**

| Name | Type |
| :--- | :--- |
| `pub_key` | [PublicKey](crypto.publickey.md) |
| `priv_key?` | [PrivateKey](crypto.privatekey.md) |

**Returns**

`Promise`&lt;[CryptoCtx](crypto.cryptoctx.md)&gt;

**Defined in**

[yajsapi/crypto.ts:73](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L73)

