# Class: SubmissionState

[yajsapi](../yajsapi.md) / [Exports](../modules/) / [executor](../modules/executor.md) / SubmissionState

## Class: SubmissionState

[executor](../modules/executor.md).SubmissionState

### Table of contents

#### Constructors

* [constructor](executor.submissionstate.md#constructor)

#### Properties

* [agreements\_pool](executor.submissionstate.md#agreements_pool)
* [builder](executor.submissionstate.md#builder)
* [offers\_collected](executor.submissionstate.md#offers_collected)
* [payment\_cancellation\_token](executor.submissionstate.md#payment_cancellation_token)
* [proposals\_confirmed](executor.submissionstate.md#proposals_confirmed)
* [worker\_cancellation\_token](executor.submissionstate.md#worker_cancellation_token)

### Constructors

#### constructor

• **new SubmissionState**\(`builder`, `agreements_pool`\)

**Parameters**

| Name | Type |
| :--- | :--- |
| `builder` | [DemandBuilder](props_builder.demandbuilder.md) |
| `agreements_pool` | [AgreementsPool](executor_agreements_pool.agreementspool.md) |

**Defined in**

[yajsapi/executor/index.ts:133](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L133)

### Properties

#### agreements\_pool

• **agreements\_pool**: [AgreementsPool](executor_agreements_pool.agreementspool.md)

**Defined in**

[yajsapi/executor/index.ts:129](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L129)

#### builder

• **builder**: [DemandBuilder](props_builder.demandbuilder.md)

**Defined in**

[yajsapi/executor/index.ts:128](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L128)

#### offers\_collected

• **offers\_collected**: `number` = 0

**Defined in**

[yajsapi/executor/index.ts:130](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L130)

#### payment\_cancellation\_token

• **payment\_cancellation\_token**: [default](utils_cancellationtoken.default.md)

**Defined in**

[yajsapi/executor/index.ts:132](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L132)

#### proposals\_confirmed

• **proposals\_confirmed**: `number` = 0

**Defined in**

[yajsapi/executor/index.ts:131](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L131)

#### worker\_cancellation\_token

• **worker\_cancellation\_token**: [default](utils_cancellationtoken.default.md)

**Defined in**

[yajsapi/executor/index.ts:133](https://github.com/golemfactory/yajsapi/blob/8f42a91/yajsapi/executor/index.ts#L133)

