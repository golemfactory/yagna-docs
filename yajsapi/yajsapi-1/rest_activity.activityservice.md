# rest/activity/activityservice

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/9699eb3e934dbc2c15063c37bc7a317a2c47fef4/yajsapi/modules.md) / [rest/activity](../yajsapi-2/rest_activity.md) / ActivityService

## Class: ActivityService

[rest/activity](../yajsapi-2/rest_activity.md).ActivityService

A convenience helper to facilitate the creation of an Activity.

### Hierarchy

* **ActivityService**

### Table of contents

#### Constructors

* [constructor](rest_activity.activityservice.md#constructor)

#### Properties

* [\_api](rest_activity.activityservice.md#_api)
* [\_state](rest_activity.activityservice.md#_state)

#### Methods

* [\_attest](rest_activity.activityservice.md#_attest)
* [\_create\_activity](rest_activity.activityservice.md#_create_activity)
* [\_create\_secure\_activity](rest_activity.activityservice.md#_create_secure_activity)
* [new\_activity](rest_activity.activityservice.md#new_activity)

### Constructors

#### constructor

+ **new ActivityService**\(`cfg`: _Configuration_\): [_ActivityService_](rest_activity.activityservice.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cfg` | _Configuration_ |

**Returns:** [_ActivityService_](rest_activity.activityservice.md)

Defined in: [yajsapi/rest/activity.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L28)

### Properties

#### \_api

• `Private` **\_api**: _RequestorControlApi_

Defined in: [yajsapi/rest/activity.ts:27](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L27)

#### \_state

• `Private` **\_state**: _RequestorStateApi_

Defined in: [yajsapi/rest/activity.ts:28](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L28)

### Methods

#### \_attest

▸ **\_attest**\(`activity_id`: _string_, `agreement`: [_Agreement_](rest_market.agreement.md), `credentials`: Credentials\): _Promise_&lt;_void_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `activity_id` | _string_ |
| `agreement` | [_Agreement_](rest_market.agreement.md) |
| `credentials` | Credentials |

**Returns:** _Promise_&lt;_void_&gt;

Defined in: [yajsapi/rest/activity.ts:108](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L108)

#### \_create\_activity

▸ **\_create\_activity**\(`agreement_id`: _string_\): _Promise_&lt;_Activity_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `agreement_id` | _string_ |

**Returns:** _Promise_&lt;_Activity_&gt;

Defined in: [yajsapi/rest/activity.ts:58](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L58)

#### \_create\_secure\_activity

▸ **\_create\_secure\_activity**\(`agreement`: [_Agreement_](rest_market.agreement.md)\): _Promise_&lt;_SecureActivity_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `agreement` | [_Agreement_](rest_market.agreement.md) |

**Returns:** _Promise_&lt;_SecureActivity_&gt;

Defined in: [yajsapi/rest/activity.ts:65](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L65)

#### new\_activity

▸ **new\_activity**\(`agreement`: [_Agreement_](rest_market.agreement.md), `secure?`: _boolean_\): _Promise_&lt;_Activity_&gt;

Create an activity within bounds of the specified agreement.

**Parameters:**

| Name | Type | Default value | Description |
| :--- | :--- | :--- | :--- |
| `agreement` | [_Agreement_](rest_market.agreement.md) | - | - |
| `secure` | _boolean_ | false | - |

**Returns:** _Promise_&lt;_Activity_&gt;

Activity

Defined in: [yajsapi/rest/activity.ts:42](https://github.com/golemfactory/yajsapi/blob/0a8d8c8/yajsapi/rest/activity.ts#L42)

