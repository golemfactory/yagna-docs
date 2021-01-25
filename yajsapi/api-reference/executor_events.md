# executor/events

[yajsapi](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/README.md) / [Exports](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/modules.md) / executor/events

## Module: executor/events

### Table of contents

#### Classes

* [ActivityCreateFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.activitycreatefailed.md)
* [ActivityCreated](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.activitycreated.md)
* [AgreementConfirmed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.agreementconfirmed.md)
* [AgreementCreated](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.agreementcreated.md)
* [AgreementRejected](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.agreementrejected.md)
* [AgreementTerminated](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.agreementterminated.md)
* [CheckingPayments](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.checkingpayments.md)
* [CollectFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.collectfailed.md)
* [CommandEvent](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandevent.md)
* [CommandEventContext](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandeventcontext.md)
* [CommandExecuted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandexecuted.md)
* [CommandStarted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandstarted.md)
* [CommandStdErr](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandstderr.md)
* [CommandStdOut](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.commandstdout.md)
* [ComputationFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.computationfailed.md)
* [ComputationFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.computationfinished.md)
* [ComputationStarted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.computationstarted.md)
* [DownloadFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.downloadfinished.md)
* [DownloadStarted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.downloadstarted.md)
* [GettingResults](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.gettingresults.md)
* [InvoiceReceived](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.invoicereceived.md)
* [NoProposalsConfirmed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.noproposalsconfirmed.md)
* [PaymentAccepted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.paymentaccepted.md)
* [PaymentFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.paymentfailed.md)
* [PaymentPrepared](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.paymentprepared.md)
* [PaymentQueued](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.paymentqueued.md)
* [PaymentsFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.paymentsfinished.md)
* [ProposalConfirmed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.proposalconfirmed.md)
* [ProposalFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.proposalfailed.md)
* [ProposalReceived](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.proposalreceived.md)
* [ProposalRejected](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.proposalrejected.md)
* [ProposalResponded](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.proposalresponded.md)
* [ScriptFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.scriptfinished.md)
* [ScriptSent](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.scriptsent.md)
* [ShutdownFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.shutdownfinished.md)
* [SubscriptionCreated](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.subscriptioncreated.md)
* [SubscriptionFailed](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.subscriptionfailed.md)
* [TaskAccepted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.taskaccepted.md)
* [TaskRejected](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.taskrejected.md)
* [TaskStarted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.taskstarted.md)
* [WorkerFinished](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.workerfinished.md)
* [WorkerStarted](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.workerstarted.md)
* [YaEvent](https://github.com/golemfactory/yagna-docs/tree/1b9d66c57da52a346eb2988dcfe9aa00d2f3d587/yajsapi/classes/executor_events.yaevent.md)

