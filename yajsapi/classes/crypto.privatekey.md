# Class: PrivateKey

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [crypto](../modules/crypto.md) / PrivateKey

## Class: PrivateKey

[crypto](../modules/crypto.md).PrivateKey

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

• **new PrivateKey**\(\)

**Defined in**

[yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L11)

### Properties

#### inner

• **inner**: `Buffer`

**Defined in**

[yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L11)

### Methods

#### derive

▸ **derive**\(`publicKey`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `publicKey` | [PublicKey](crypto.publickey.md) |

**Returns**

`Promise`

**Defined in**

[yajsapi/crypto.ts:35](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L35)

#### publicKey

▸ **publicKey**\(`compressed?`\): [PublicKey](crypto.publickey.md)

**Parameters**

| Name | Type | Default value |
| :--- | :--- | :--- |
| `compressed` | `boolean` | true |

**Returns**

[PublicKey](crypto.publickey.md)

**Defined in**

[yajsapi/crypto.ts:28](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L28)

#### sign

▸ **sign**\(`msg`\): `Promise`

**Parameters**

| Name | Type |
| :--- | :--- |
| `msg` | `Buffer` |

**Returns**

`Promise`

**Defined in**

[yajsapi/crypto.ts:39](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L39)

#### toString

▸ **toString**\(\): `string`

**Returns**

`string`

**Defined in**

[yajsapi/crypto.ts:43](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L43)

#### from

▸ `Static` **from**\(`buffer`\): [PrivateKey](crypto.privatekey.md)

**Parameters**

| Name | Type |
| :--- | :--- |
| `buffer` | `Buffer` |

**Returns**

[PrivateKey](crypto.privatekey.md)

**Defined in**

[yajsapi/crypto.ts:17](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L17)

#### fromHex

▸ `Static` **fromHex**\(`hex`\): [PublicKey](crypto.publickey.md)

**Parameters**

| Name | Type |
| :--- | :--- |
| `hex` | `string` |

**Returns**

[PublicKey](crypto.publickey.md)

**Defined in**

[yajsapi/crypto.ts:23](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/crypto.ts#L23)

