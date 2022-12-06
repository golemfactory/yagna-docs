---
description: Symptoms and solutions of known issues.
---

# Requestor Troubleshooting

{% hint style="info" %}
#### Requestor Issues

Don't miss the [debugging section by using the log file](../requestor-tutorials/debugging.md#reading-the-log-file).
{% endhint %}

## IO error: No such file or directory

_**Os:**_ Any

_**Description:**_ Local service error: Transfer error: IO error: No such file or directory (os error 2)

_**Solution:**_ Something went wrong with the computation. We have a "[Debugging with the use of log files](https://handbook.golem.network/requestor-tutorials/debugging)" guide in our requestor tutorials to assist with debugging.

You can also check that you're [defining your task's](https://handbook.golem.network/requestor-tutorials/golem-application-fundamentals/hl-api-work-generator-pattern) correctly and that you remembered to define a place (or places) in the container file system that will be used for the file transfer, [as discussed here](https://handbook.golem.network/requestor-tutorials/golem-application-fundamentals#input-and-output).

With `ctx.run()` make sure that you don't have multiple arguments in one string. Either `ctx.run("/bin/sh", "-c", "a", "b", "c" ...)` or use the syntax the [example gives](../requestor-tutorials/task-processing-development/task-example-2-hashcat.md#the-requestor-agent-code) where it parses in lines.

## Send error: send failed because receiver is gone

If you manage to receive a message that says:

`Activity failed on provider [..] failed on provider with message 'Local service error: Transfer error: Send error: send failed because receiver is gone'`

That most likely means you're trying to send a transfer command (`upload_file` / `download_file`) to/from a location that's not a VOLUME. The reason is that only the volumes are accessible to the exe unit runner and other locations in the image simply cannot be read or written to.

## Symlink issues

_**Os:** Ubuntu_

_**Description:**_ If you run the Golem Provider one-line installer on a minimal install of Ubuntu and it completes without error but doesn't run then you might have a `symlink` issue.

_**Solution:** See_ [_this guide_](https://websiteforstudents.com/setup-and-manage-symlinks-on-ubuntu-18-04-16-04/) _on setting up and managing Simlinks._

## Connectivity issue

_**Os:** All_

_**Description:**_ When someone is not receiving tasks at all, has correct subnet configured, and VM valid, the most probable cause is yagna "connectivity" issue

_**Solution:**_ Kill and restart the process

## Payment driver initialization issue

_**Os:**_ All, requestor only

_**Description:**_ Since our newest addition to Golem - the integration with zkSync, layer 2 payment solution - is, so far, a highly experimental feature, it may still sometimes happen that the yagna daemon fails to initialize itself correctly.

This will manifest itself either by a failure of the regular initialization with`yagna payment fund` or through an error you'll receive when running `yagna payment status`.

_**Solution:**_ In such a case, we're providing you with a fallback to normal payments, i.e. regular GLM token transfer on the Ethereum chain.

To enable it run:

```
yagna payment fund --driver erc20
yagna payment status --driver erc20
yagna payment init --sender --driver erc20
```

After you confirm you have the funds, proceed with running the examples or your own requestor agent code normally. The providers are configured to accept both zkSync and the regular tokens and will adjust accordingly.

Just remember to use [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io) instead of the zkSync explorer, should you wish to verify that the payment went through.

## Bind error: already registered

_**Os:** Ubuntu_

_**Description:**_ If the user has an obsolete/incorrect version of `gftp` in `$PATH` they will get a repeating error when they try to request a task:

```
[2020-11-27 15:43:11,509 INFO yapapi.summary] Received proposals from 9 providers so far
[2020-11-27T14:43:12Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID '/public/gftp/ee82d5dc7188611da558c76e777a2df7867d9526eac6fa9378728d44ca4a2a10/GetMetadata' already registered
[2020-11-27T14:43:12Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID '/public/gftp/ee82d5dc7188611da558c76e777a2df7867d9526eac6fa9378728d44ca4a2a10/GetChunk' already registered
[2020-11-27 15:43:12,434 WARNING yapapi.summary] Activity failed on provider 'odra.3', reason: (-32000, "bad request: No service registered under given address '/private/identity/Get'.", {'jsonrpc': '2.0', 'id': 4622765855815754544, 'error': {'code': -32000, 'message': "bad request: No service registered under given address '/private/identity/Get'."}})
[2020-11-27 15:43:12,592 INFO yapapi.summary] Agreement proposed to provider 'ada'
[2020-11-27 15:43:13,961 INFO yapapi.summary] Agreement confirmed by provider 'ada'
[2020-11-27T14:43:15Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID '/public/gftp/ee82d5dc7188611da558c76e777a2df7867d9526eac6fa9378728d44ca4a2a10/GetMetadata' already registered
[2020-11-27T14:43:15Z ERROR ya_service_bus::remote_router] bind error: already registered: Service ID '/public/gftp/ee82d5dc7188611da558c76e777a2df7867d9526eac6fa9378728d44ca4a2a10/GetChunk' already registered
[2020-11-27 15:43:15,199 WARNING yapapi.summary] Activity failed on provider 'ada', reason: (-32000, "bad request: No service registered under given address '/private/identity/Get'.", {'jsonrpc': '2.0', 'id': 1935240589707464482, 'error': {'code': -32000, 'message': "bad request: No service registered under given address '/private/identity/Get'."}})
```

_**Solution:**_ Type `which gftp` to find the obsolete version of `gftp` and then remove it. Then restart your daemon and the issue should be fixed!

## Installation process terminated: SSL verification failure

_**Os:**_ All

_**Description:**_ If the user runs `golem-installer` having an incorrect system date/time set, the installation process breaks out with an error. The failure message states that an SSL certificate validation problem has occurred:

```
golem-installer: installing to /home/user/.local/bin
 Component                             Version
-----------               --------------------
golem core                              0.10.0 curl: (60) SSL certificate problem: certificate is not yet valid
More details here: https://curl.haxx.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.
```

_**Solution:**_ Check the clock of your machine. If the date and/or time is incorrect update it. The system clock must be set properly to prevent SSL verification failure. In order to skip verification use either `-k` or `--insecure` flag.
