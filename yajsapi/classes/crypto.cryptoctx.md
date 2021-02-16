# Class: CryptoCtx

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [crypto](../modules/crypto.md) / CryptoCtx

## Class: CryptoCtx

[crypto](../modules/crypto.md).CryptoCtx

### Hierarchy

* **CryptoCtx**

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

+ `Private`**new CryptoCtx**\(`priv_key`: [_PrivateKey_](crypto.privatekey.md), `ephem_key`: _Buffer_\): [_CryptoCtx_](crypto.cryptoctx.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `priv_key` | [_PrivateKey_](crypto.privatekey.md) |
| `ephem_key` | _Buffer_ |

**Returns:** [_CryptoCtx_](crypto.cryptoctx.md)

Defined in: [yajsapi/crypto.ts:77](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L77)

### Properties

#### ephem\_key

• **ephem\_key**: _Buffer_

Defined in: [yajsapi/crypto.ts:71](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L71)

#### priv\_key

• **priv\_key**: [_PrivateKey_](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:70](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L70)

### Methods

#### decrypt

▸ **decrypt**\(`data`: _Buffer_\): _Buffer_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `data` | _Buffer_ |

**Returns:** _Buffer_

Defined in: [yajsapi/crypto.ts:106](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L106)

#### encrypt

▸ **encrypt**\(`data`: _Buffer_\): _Buffer_

**Parameters:**

| Name | Type |
| :--- | :--- |
| `data` | _Buffer_ |

**Returns:** _Buffer_

Defined in: [yajsapi/crypto.ts:84](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L84)

#### from

▸ `Static`**from**\(`pub_key`: [_PublicKey_](crypto.publickey.md), `priv_key?`: [_PrivateKey_](crypto.privatekey.md)\): _Promise_&lt;[_CryptoCtx_](crypto.cryptoctx.md)&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `pub_key` | [_PublicKey_](crypto.publickey.md) |
| `priv_key?` | [_PrivateKey_](crypto.privatekey.md) |

**Returns:** _Promise_&lt;[_CryptoCtx_](crypto.cryptoctx.md)&gt;

Defined in: [yajsapi/crypto.ts:73](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/crypto.ts#L73)

