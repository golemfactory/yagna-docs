# utils/asyncexitstack.default

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [utils/asyncExitStack](../yajsapi-2/utils_asyncexitstack.md) / default

## Class: default

[utils/asyncExitStack](../yajsapi-2/utils_asyncexitstack.md).default

### Hierarchy

* **default**

### Table of contents

#### Constructors

* [constructor](utils_asyncexitstack.default.md#constructor)

#### Properties

* [\_stack](utils_asyncexitstack.default.md#_stack)

#### Methods

* [aclose](utils_asyncexitstack.default.md#aclose)
* [enter\_async\_context](utils_asyncexitstack.default.md#enter_async_context)

### Constructors

#### constructor

+ **new default**\(\): [_default_](utils_asyncexitstack.default.md)

**Returns:** [_default_](utils_asyncexitstack.default.md)

### Properties

#### \_stack

• `Private` **\_stack**: _any_\[\]

Defined in: [yajsapi/utils/asyncExitStack.ts:2](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncExitStack.ts#L2)

### Methods

#### aclose

▸ **aclose**\(\): _Promise_&lt;_void_&gt;

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/utils/asyncExitStack.ts:9](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncExitStack.ts#L9)

#### enter\_async\_context

▸ **enter\_async\_context**\(`ctx`: _any_\): _Promise_&lt;_any_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `ctx` | _any_ |

**Returns:** _Promise_&lt;_any_&gt;

Defined in: [yajsapi/utils/asyncExitStack.ts:3](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/utils/asyncExitStack.ts#L3)

