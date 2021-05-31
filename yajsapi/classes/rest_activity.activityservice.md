# Class: ActivityService

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [rest/activity](../modules/rest_activity.md) / ActivityService

## Class: ActivityService

[rest/activity](../modules/rest_activity.md).ActivityService

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

* **new ActivityService**\(`cfg`: _Configuration_\): [_ActivityService_](rest_activity.activityservice.md)

**Parameters:**

| Name | Type |
| :--- | :--- |
| `cfg` | _Configuration_ |

**Returns:** [_ActivityService_](rest_activity.activityservice.md)

Defined in: [yajsapi/rest/activity.ts:29](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L29)

### Properties

#### \_api

• `Private` **\_api**: _RequestorControlApi_

Defined in: [yajsapi/rest/activity.ts:28](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L28)

#### \_state

• `Private` **\_state**: _RequestorStateApi_

Defined in: [yajsapi/rest/activity.ts:29](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L29)

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

Defined in: [yajsapi/rest/activity.ts:109](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L109)

#### \_create\_activity

▸ **\_create\_activity**\(`agreement_id`: _string_\): _Promise_&lt;_Activity_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `agreement_id` | _string_ |

**Returns:** _Promise_&lt;_Activity_&gt;

Defined in: [yajsapi/rest/activity.ts:59](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L59)

#### \_create\_secure\_activity

▸ **\_create\_secure\_activity**\(`agreement`: [_Agreement_](rest_market.agreement.md)\): _Promise_&lt;_SecureActivity_&gt;

**Parameters:**

| Name | Type |
| :--- | :--- |
| `agreement` | [_Agreement_](rest_market.agreement.md) |

**Returns:** _Promise_&lt;_SecureActivity_&gt;

Defined in: [yajsapi/rest/activity.ts:66](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L66)

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

Defined in: [yajsapi/rest/activity.ts:43](https://github.com/golemfactory/yajsapi/blob/289a25a/yajsapi/rest/activity.ts#L43)

