# Getting started to write L2 payment driver for Yagna

This document aims to provide guidelines to develop a payment driver based on boilerplate code from [Yagna repository](https://github.com/golemfactory/yagna). It assumes reader has some experience in [Rust language](https://www.rust-lang.org/) and also Yagna project's codebase. We're providing an information for payment driver that will be integrated into Yagna daemon codebase and gains from reusing a lot of already provided components. It's also possible to develop stand-alone driver application that communicates with the Yagna daemon via TCP, but it won't be described here.


## Overview

Payment service of Yagna daemon expects that payment driver will handle all communication with particular L2 network provider (but it's not limited to Ethereum ecosystem).
You might assume that payment driver should:

- communicate with daemon services over Golem Service Bus (GSB),
- provide operation like deposits, exits, transfer, account unlocking,
- delegate transaction's signing to the Identity service,
- notify Payment service about committed transactions,
- retry operations that failed to due non-critical causes.


## Codebase

Clone [Yagna](https://github.com/golemfactory/yagna) git repository from GitHub. 
Most interesting parts are located in `core/payment-driver` directory. 
Here's what can be find there:

- `core/payment-driver/base` - base driver components which defines database schema and operations, registers to GSB events, helps with creation of background jobs and some utility code.
- `core/payment-driver/zksync` - provides a reference driver implementation of [Zk-Sync](https://zksync.io) L2 network.
- `core/payment-driver/base/driver.rs` - declares a Rust's trait that a new driver hast to implement
- `core/payment-driver/base/cron.rs` - declares a driver's periodical operation trait.
-  - declares the driver's operations to other daemon services, e.g. `register_account`, `sign`, `notify_payment`.
 

## Implementation details

Let's see what a driver's trait exposes:

- `init` - Initializes the account to be used with the driver service. It should call `bus::register_account` to notify Payment service about the driver readiness. Driver can handle multiple accounts.
- `enter` - Deposits the funds into the driver's supported network. Called by CLI.
- `exit` - Exits the funds outside the driver's supported network (most likely L1). Called by CLI.
- `get_account_balance` - Gets the balance of the account.
- `transfer` - Transfers the funds between specified accounts. Called by CLI.
- `get_transaction_balance` - Deprecated. Drivers should return very big number (e.g. `1_000_000_000_000_000_000u64` or the whole token supply).
- `schedule_payment` - Schedules the payment between specified accounts. Payments are processed by the `cron` job. Payment tracking is done by cron job, see: `PaymentDriverCron::confirm_payments`. Returns an `order_id`. See also `notify_payment`
- `verify_payment` - Verifies the payment transaction specified by transaction's hash.
- `validate_allocation` - Validates that allocated funds are still sufficient to cover the costs of the task (including the Gas cost). Allocation is created when the requestor publishes the task on the market.
- `account_event` - Called by the Identity service to notify the driver that specified account is _locked_ / _unlocked_. Identity service holds accounts private keys and signs transactions.
- `recv_init_required` - Tells whether account initialization is needed for receiving payments.

The following driver's operations are processed periodically by the cron jobs. The following `PaymentDriverCron` trait needs to be implemented.

- `confirm_payments` - Confirms scheduled payments.
- `process_payments` - Processes scheduled payments.

The payment driver receives all requests via the GSB. This is also a communication channel to call other services. See `core/payment-driver/base/bus.rs` file.

- `register_account` - /// Notifies the Payment service that the account is ready to sending / receiving funds. See `init` above.
- `sign` - Delegates signing of the transaction's payload to the Identity service.
- `notify_payment` - Notifies the Payment service that the scheduled payment is processed successfully. It also links the `order_id` with the `confirmation` (e.g. transaction's hash). See `schedule_payment` above.

