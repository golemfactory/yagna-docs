[yajsapi](../README.md) / [Exports](../modules.md) / [crypto](../modules/crypto.md) / PrivateKey

# Class: PrivateKey

[crypto](../modules/crypto.md).PrivateKey

## Hierarchy

* **PrivateKey**

## Table of contents

### Constructors

- [constructor](crypto.privatekey.md#constructor)

### Properties

- [inner](crypto.privatekey.md#inner)

### Methods

- [derive](crypto.privatekey.md#derive)
- [publicKey](crypto.privatekey.md#publickey)
- [sign](crypto.privatekey.md#sign)
- [toString](crypto.privatekey.md#tostring)
- [from](crypto.privatekey.md#from)
- [fromHex](crypto.privatekey.md#fromhex)

## Constructors

### constructor

\+ **new PrivateKey**(): [*PrivateKey*](crypto.privatekey.md)

**Returns:** [*PrivateKey*](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L11)

## Properties

### inner

• **inner**: *Buffer*

Defined in: [yajsapi/crypto.ts:11](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L11)

## Methods

### derive

▸ **derive**(`publicKey`: [*PublicKey*](crypto.publickey.md)): *Promise*<*Buffer*\>

#### Parameters:

Name | Type |
------ | ------ |
`publicKey` | [*PublicKey*](crypto.publickey.md) |

**Returns:** *Promise*<*Buffer*\>

Defined in: [yajsapi/crypto.ts:35](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L35)

___

### publicKey

▸ **publicKey**(`compressed?`: *boolean*): [*PublicKey*](crypto.publickey.md)

#### Parameters:

Name | Type | Default value |
------ | ------ | ------ |
`compressed` | *boolean* | true |

**Returns:** [*PublicKey*](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L28)

___

### sign

▸ **sign**(`msg`: *Buffer*): *Promise*<*Buffer*\>

#### Parameters:

Name | Type |
------ | ------ |
`msg` | *Buffer* |

**Returns:** *Promise*<*Buffer*\>

Defined in: [yajsapi/crypto.ts:39](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L39)

___

### toString

▸ **toString**(): *string*

**Returns:** *string*

Defined in: [yajsapi/crypto.ts:43](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L43)

___

### from

▸ `Static`**from**(`buffer`: *Buffer*): [*PrivateKey*](crypto.privatekey.md)

#### Parameters:

Name | Type |
------ | ------ |
`buffer` | *Buffer* |

**Returns:** [*PrivateKey*](crypto.privatekey.md)

Defined in: [yajsapi/crypto.ts:17](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L17)

___

### fromHex

▸ `Static`**fromHex**(`hex`: *string*): [*PublicKey*](crypto.publickey.md)

#### Parameters:

Name | Type |
------ | ------ |
`hex` | *string* |

**Returns:** [*PublicKey*](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:23](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L23)
