# Getting started to write payment driver for Yagna

This document aims to provide guidelines to develop a payment driver based on boilerplate code from [Yagna repository](https://github.com/golemfactory/yagna). It assumes the reader has some experience in [Rust language](https://www.rust-lang.org/) and also Yagna project's codebase. We're providing an information for payment driver that will be integrated into Yagna daemon codebase and gains from reusing a lot of already provided components. It's also possible to develop stand-alone driver application that communicates with the Yagna daemon via TCP, but it won't be described here.


## Overview

Payment service of Yagna daemon expects that payment driver will handle all communication with particular L2 network provider (but it's not limited to Ethereum ecosystem).
You might assume that payment driver should:

- communicate with daemon services over Golem Service Bus (GSB),
- provide operation like deposits, exits, transfer, account unlocking,
- delegate transaction's signing to the Identity service,
- notify Payment service about committed transactions,
- retry operations that failed due to non-critical causes.

Here is a checklist that driver implementors would want to follow:

- [] Fork the Yagna repository and clone it locally to start working on the code,
- [] Create a new crate for your driver in the `core/payment-drivers` directory,
- [] Implement all methods from `PaymentDriver` trait, some of them are described in the section below,
- [] Your implementation can also benefit from database handling code and background tasks in `cron` module, but it is not mandatory to use them,
- [] Make a new driver build and start with the Yagna daemon. See instructions bellow,
- [] Test and verify it's working using instructions from the section bellow,
- [] Send us a Pull Request.


## Codebase

Clone [Yagna](https://github.com/golemfactory/yagna) git repository from GitHub. 
Most interesting parts are located in `core/payment-driver` directory. 
Here's what can be found there:

- `core/payment-driver/base` - base driver components which defines database schema and operations, registers to GSB events, helps with creation of background jobs and some utility code.
- `core/payment-driver/zksync` - provides a reference driver implementation of [Zk-Sync](https://zksync.io) L2 network.
- `core/payment-driver/base/driver.rs` - declares a Rust's trait that a new driver hast to implement
- `core/payment-driver/base/cron.rs` - declares a driver's periodical operation trait. It's optional to use it.
- `core/payment-driver/base/bus.rs` - declares the driver's operations to other daemon services, e.g. `register_account`, `sign`, `notify_payment`.
- `core/payment-driver/base/dao` - handy functions to DB (sqlite) interaction. It's optional to use it.
 

## Implementation details

Let's see what a driver's trait exposes:

- `init` - Initializes the account to be used with the driver service. It should call `bus::register_account` to notify Payment service about the driver readiness. Driver can handle multiple accounts.
- `enter` - Deposits the funds into the driver's supported network. Called by CLI.
- `exit` - Exits the funds outside the driver's supported network (most likely L1). Called by CLI.
- `get_account_balance` - Gets the balance of the account.
- `transfer` - Transfers the funds between specified accounts. Called by CLI.
- `fund` - Funds the account from faucet when run on testnet. Provides instructions how to fund on mainnet.
- `schedule_payment` - Schedules the payment between specified accounts. Payments are processed by the `cron` job. Payment tracking is done by cron job, see: `PaymentDriverCron::confirm_payments`. Returns an `order_id`. See also `notify_payment`
- `verify_payment` - Verifies the payment transaction specified by transaction's confirmation (transaction's identifier).
- `validate_allocation` - Validates that allocated funds are still sufficient to cover the costs of the task (including the transaction fees, e.g. Ethereum's Gas). Allocation is created when the requestor publishes the task on the market.
- `account_event` - Called by the Identity service to notify the driver that specified account is _locked_ / _unlocked_. Identity service holds accounts private keys and signs transactions.
- `recv_init_required` - Tells whether account initialization is needed for receiving payments.
- `get_transaction_balance` - Deprecated. Drivers should return very big number (e.g. `1_000_000_000_000_000_000u64` or the whole token supply).


The following driver's operations are processed periodically by the cron jobs. It is not mandatory to implement `PaymentDriverCron` trait as long as the driver can operate without the cron.

- `confirm_payments` - Confirms scheduled payments.
- `process_payments` - Processes scheduled payments.

The payment driver receives all requests via the GSB. This is also a communication channel to call other services. See `core/payment-driver/base/bus.rs` file.

- `register_account` - Notifies the Payment service that the account is ready to sending / receiving funds. See `init` above.
- `sign` - Delegates signing of the transaction's payload to the Identity service.
- `notify_payment` - Notifies the Payment service that the scheduled payment is processed successfully. It also links the `order_id` with the `confirmation` (e.g. transaction's hash). See `schedule_payment` above. This notification leads to `verify_payment` call on the provider side.

## Starting a new driver with Yagna

Add a new block in `start_payment_drivers` function in [`core/serv/src/main.rs`](https://github.com/golemfactory/yagna/blob/master/core/serv/src/main.rs#L216) file.
It should follow the convention and declares its own compilation flag. Don't forget to set this flag during the compilation :wink:.

## Testing a new driver

When you consider your work is done, take some time to actually see it in action. Be sure we will scrupulously test the driver behavior in the following scenarios, including the error messages written in logs and returned from CLI. Don't hesitate to ask questions, we are here to help.  

We will run the following tests (happy paths and providing invalid parameters to make it fail).

- command line interaction with the driver: `init`, `fund`, `enter`, `transfer`, `status`,  `exit` ...
- [quickstart tutorial](https://golem-network.gitbook.io/golem-sdk-develop/requestor-tutorials/flash-tutorial-of-requestor-development) with the blender example task,
- review made transactions in the corresponding block explorer.

## Running Payment service examples

As another option to testing is to run [Payment service examples](https://github.com/golemfactory/yagna/blob/master/core/payment/examples/README.md) against new driver. There's a bit of hassle to set up the test, so I'll describe it here.

1. Enable your driver in the example's [`payment_api` enum](https://github.com/golemfactory/yagna/blob/635fac0eda514c7359928851323affa254116d71/core/payment/examples/payment_api.rs#L30) and resolve compilation errors in the following `match` expressions.

1. Start an example payment service (each test assumes running from scratch) <br/>`
rm payment.db* && cargo run --example payment_api -- --driver=<DRIVER> --platform=<PLATFORM>`

1. Start _invoice flow_ example (restart above `platform_api` on each test) <br/>`
cargo run --example invoice_flow -- --platform=<PLATFORM>`

1. Start _debit note flow_ example (restart above `platform_api` on each test) <br/>`
cargo run --example debit_note_flow -- --platform=<PLATFORM>`

1. Don't be afraid to try other examples as well ;)
