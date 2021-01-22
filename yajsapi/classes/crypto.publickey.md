[yajsapi](../README.md) / [Exports](../modules.md) / [crypto](../modules/crypto.md) / PublicKey

# Class: PublicKey

[crypto](../modules/crypto.md).PublicKey

## Hierarchy

* **PublicKey**

## Table of contents

### Constructors

- [constructor](crypto.publickey.md#constructor)

### Properties

- [inner](crypto.publickey.md#inner)

### Methods

- [toString](crypto.publickey.md#tostring)
- [from](crypto.publickey.md#from)
- [fromHex](crypto.publickey.md#fromhex)

## Constructors

### constructor

\+ `Private`**new PublicKey**(): [*PublicKey*](crypto.publickey.md)

**Returns:** [*PublicKey*](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:49](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L49)

## Properties

### inner

• **inner**: *Buffer*

Defined in: [yajsapi/crypto.ts:49](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L49)

## Methods

### toString

▸ **toString**(): *string*

**Returns:** *string*

Defined in: [yajsapi/crypto.ts:64](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L64)

___

### from

▸ `Static`**from**(`buffer`: *Buffer*): [*PublicKey*](crypto.publickey.md)

#### Parameters:

Name | Type |
------ | ------ |
`buffer` | *Buffer* |

**Returns:** [*PublicKey*](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:53](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L53)

___

### fromHex

▸ `Static`**fromHex**(`hex`: *string*): [*PublicKey*](crypto.publickey.md)

#### Parameters:

Name | Type |
------ | ------ |
`hex` | *string* |

**Returns:** [*PublicKey*](crypto.publickey.md)

Defined in: [yajsapi/crypto.ts:59](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/crypto.ts#L59)
