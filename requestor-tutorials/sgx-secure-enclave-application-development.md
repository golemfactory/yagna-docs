# SGX secure enclave application development

## Introduction

We use the Game of roulette application as golem based SGX development example. The game is executed in an Intel \(R\) SGX secure enclave where no player is required to trust the game host. Each game interaction is cryptographically verified with enclave's credentials to ensure that the result has been computed in a trusted execution environment.

## Prerequisites

* [`node`](https://nodejs.org/en/download/) v12 \(LTS\) or newer
* Firefox / Chrome web browser with a [MetaMask](https://metamask.io/download.html) plugin installed

## Building

* Clone [https://github.com/golemfactory/ya-as-sgx-examples](https://github.com/golemfactory/ya-as-sgx-examples)

`git clone https://github.com/golemfactory/ya-as-sgx-examples`

* Install project dependencies with:

`npm install` or `yarn install`

* Build typescript sources:

`npm run build` or `yarn build`

## Running

* Run `yagna` as described in the

{% page-ref page="flash-tutorial-of-requestor-development.md" %}

{% hint style="success" %}
So now, we're going to assume that:

* The `yagna` deamon is running in the background. 
* The `YAGNA_APPKEY` environment variable is set to the value of the generated app key.
{% endhint %}

Now you need to setup `SUBNET` system variable to point to the `devnet.alpha.3`

{% tabs %}
{% tab title="Ubuntu / mac OS X" %}
```text
export SUBNET=devnet.alpha.3
```
{% endtab %}

{% tab title="Windows" %}
```text
set SUBNET=devnet.alpha.3
```
{% endtab %}
{% endtabs %}

Now open your browser and visit [http://localhost:8000](http://localhost:8000/).

## Overview

This codebase consists of 3 main modules:

* **HTTP & JSON API server**
  * exposes JSON API endpoints where users can request the game's status, place bets, and spin the wheel
  * serves static web UI assets
  * forwards end-user actions to the yagna requestor
* \*\*\*\*[**`yagna`**](https://handbook.golem.network/introduction/golem-overview#golem-architecture) **requestor**
  * spawns game servers in SGX enclaves on providers' machines in Golem network
  * mediates communication between the game server and the JSON API endpoint
* **Web UI**
  * provides a convenient way of interacting with the JSON API
  * signs client requests with an Ethereum account, unlocked at the time in the MetaMask plugin
  * cryptographically verifies game server responses and presents them to the user

These modules are executed asynchronously in a single-threaded node application.

## **HTTP & JSON API server**

Implements communication channels that allow to synchronously await for responses to game client's actions.

## Requestor

In order of execution, the requestor:

1. Joins the Golem marketplace and publishes a demand for executing the game server in an SGX enclave
2. At the marketplace, negotiates hardware resources and prices and in turn locates capable providers
3. Spawns an enclave on a provider's machine with appropriate game server metadata
4. Ensures that the code is running in an SGX enclave by verifying Intel's \(R\) Attestation Service report
5. Ensures that the enclave has set up temporary keys \(secp256k1\) for signing game server responses and establishing an E2E encrypted channel to the requestor

The requestor can now execute commands inside an enclave. Initially, the game server's binary will be downloaded, verified and executed. Afterwards, commands are forwarded to the game server itself. A new instance of the game is created and its ID presented to end-users.

The requestor will now await clients' actions to execute in their name. Each action is uniquely signed by a user, verified by the game server, so that no other party can act in that user's name. All communication between the requestor and the enclave will be encrypted so that it's unintelligible to providers themselves and understood only by the code executed in an enclave.

When a game server handles user's requests, the execution output is recorded, signed and sent back to that user. Enclave's key is known and verified by users beforehand.

## Web UI

When loaded by the browser, the JavaScript code attempts to:

1. Unlock an Ethereum account via the MetaMask plugin
2. Check the game status via the JSON RPC endpoint. If a game has been created, request enclave attestation details and verify them
3. Initialize local game state

The ethereum account and game statuses are displayed at the top of the page.

After the initialization completes successfully, the user is expected to interact with the form below the status boxes:

* **Bet**

Placing a bet requires filling appropriate fields and the user will be notified when he enters an invalid value.

* **Spin**

The UI allows users to spin the roulette wheel only after placing a bet but it's not enforced by the JSON API.

{% hint style="info" %}
Clicking the submit button will prompt the user to sign her request via the MetaMask plugin.
{% endhint %}

If any of the users within a game instance request to spin, the game server will draw a number from the roulette wheel and resolve all placed bets. A result message \(winning or losing\) will be presented to the user.

Each of the game server's responses is signed within the enclave and verified by the code running in the browser.

## Limitations

Game sessions are limited to 25 minutes.

