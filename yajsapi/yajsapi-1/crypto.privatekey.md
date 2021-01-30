# crypto/privatekey

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [crypto](../yajsapi-2/crypto.md) / PrivateKey

## Class: PrivateKey

[crypto](../yajsapi-2/crypto.md).PrivateKey

### Hierarchy

* **PrivateKey**

### Table of contents

#### Constructors

* [constructor](crypto.privatekey.md#constructor)

#### Properties

* [inner](crypto.privatekey.md#inner)

#### Methods

* [derive](crypto.privatekey.md#derive)
* [publicKey](crypto.privatekey.md#publickey)
* [sign](crypto.privatekey.md#sign)
* [toString](crypto.privatekey.md#tostring)
* [from](crypto.privatekey.md#from)
* [fromHex](crypto.privatekey.md#fromhex)

### Constructors

#### constructor

+ **new PrivateKey**\(\): [_PrivateKey_](crypto.privatekey.md)

**Returns:** [_PrivateKey_](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L11)

### Properties

#### inner

• **inner**: _Buffer_

Defined in: [yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L11)

### Methods

#### derive

▸ **derive**\(`publicKey`: [_PublicKey_](crypto.publickey.md)\): _Promise_&lt;_Buffer_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `publicKey` | [_PublicKey_](crypto.publickey.md) |

**Returns:** _Promise_&lt;_Buffer_&gt;

Defined in: [yajsapi/crypto.ts:35](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L35)

#### publicKey

▸ **publicKey**\(`compressed?`: _boolean_\): [_PublicKey_](crypto.publickey.md)

**Parameters:**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `compressed` | _boolean_ | true |

**Returns:** [_PublicKey_](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L28)

#### sign

▸ **sign**\(`msg`: _Buffer_\): _Promise_&lt;_Buffer_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `msg` | _Buffer_ |

**Returns:** _Promise_&lt;_Buffer_&gt;

Defined in: [yajsapi/crypto.ts:39](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L39)

#### toString

▸ **toString**\(\): _string_

**Returns:** _string_

Defined in: [yajsapi/crypto.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L43)

#### from

▸ `Static`**from**\(`buffer`: _Buffer_\): [_PrivateKey_](crypto.privatekey.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `buffer` | _Buffer_ |

**Returns:** [_PrivateKey_](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L17)

#### fromHex

▸ `Static`**fromHex**\(`hex`: _string_\): [_PublicKey_](crypto.publickey.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `hex` | _string_ |

**Returns:** [_PublicKey_](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:23](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L23)

