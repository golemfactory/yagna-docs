# crypto/publickey

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [crypto](../yajsapi-2/crypto.md) / PublicKey

## Class: PublicKey

[crypto](../yajsapi-2/crypto.md).PublicKey

### Hierarchy

* **PublicKey**

### Table of contents

#### Constructors

* [constructor](crypto.publickey.md#constructor)

#### Properties

* [inner](crypto.publickey.md#inner)

#### Methods

* [toString](crypto.publickey.md#tostring)
* [from](crypto.publickey.md#from)
* [fromHex](crypto.publickey.md#fromhex)

### Constructors

#### constructor

+ `Private`**new PublicKey**\(\): [_PublicKey_](crypto.publickey.md)

**Returns:** [_PublicKey_](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:49](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L49)

### Properties

#### inner

• **inner**: _Buffer_

Defined in: [yajsapi/crypto.ts:49](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L49)

### Methods

#### toString

▸ **toString**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/crypto.ts:64](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L64)

#### from

▸ `Static`**from**\(`buffer`: _Buffer_\): [_PublicKey_](crypto.publickey.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `buffer` | _Buffer_ |

**Returns:** [_PublicKey_](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:53](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L53)

#### fromHex

▸ `Static`**fromHex**\(`hex`: _string_\): [_PublicKey_](crypto.publickey.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `hex` | _string_ |

**Returns:** [_PublicKey_](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:59](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L59)

