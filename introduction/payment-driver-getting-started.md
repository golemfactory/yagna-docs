# Getting started to write L2 payment driver for Yagna

This document aims to provide guidelines to develop a payment driver based on boilerplate code from [Yagna repository](https://github.com/golemfactory/yagna). It assumes reader has some experience in [Rust language](https://www.rust-lang.org/) and also Yagna project's codebase. We're providing an information for payment driver that will be integrated into Yagna daemon codebase and gains from reusing a lot of already provided components. It's also possible to develop stand-alone driver application that communicates with the Yagna daemon via TCP, but it won't be described here.


## Overview

Payment service of Yagna daemon keeps track of invoices and payment notices. They specify among the others an amount, a currency and a payment method for the particular provider's job. To be able to make a transfer of funds from requestor to the provider satisfying a particular payment method, payment service sends a request to a payment driver that support this method of payment.

## Codebase

Clone [Yagna](https://github.com/golemfactory/yagna) git repository from GitHub. 
Most interesting parts are located in `core/payment-driver` directory. 
Here's what can be find there:

- `core/payment-driver/base` - base driver components which defines database schema and operations, registers to GSB events, helps with creation of background jobs and some utility code.

- `core/payment-driver/base/driver.rs` - declares a rust's trait that a new driver hast to implement

- `core/payment-driver/zksync` - provides a reference driver implementation of [Zk-Sync](https://zksync.io) L2 network.
