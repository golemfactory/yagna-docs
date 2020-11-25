---
description: Symptoms and solutions of known issues.
---

# Common issues

### No access to VM

_Description:_ No access to VM

 _Solution:_ `curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh` 

Note: make sure `qemu-vm` is installed first with `apt install qemu-kvm`.

### IO error: No such file or directory

_Os:_ Any

_Description:_  Local service error: Transfer error: IO error: No such file or directory \(os error 2\)

_Solution:_  Something went wrong with the computation, the user could write a log file or doing some checks and then pulling that back instead of their output. Example: [https://discord.com/channels/684703559954333727/756161015493951600/767132601248907307](https://discord.com/channels/684703559954333727/756161015493951600/767132601248907307) Other potential solution: [https://discord.com/channels/684703559954333727/756161015493951600/769671518903992320](https://discord.com/channels/684703559954333727/756161015493951600/769671518903992320)

### Dependency issues

_Os: Ubuntu_

_Description:_ If someone has a minimal install of Ubuntu they can run into dependency issues

_Solution:_ the issue is related to `syslink`_._

### Connectivity issue

_Os: All_

_Description:_ When someone is not receiving tasks at all, has correct subnet configured, and VM valid, the most probable cause is yagna "connectivity" issue

_Solution:_ Kill and restart the process

### Payment driver initialization issue

_Os:_ All, requestor only

_Description:_ Since our newest addition to Golem - the integration with zkSync, layer 2 payment solution - is, so far, a highly experimental feature, it may still sometimes happen that the yagna daemon fails to initialize itself correctly.

This will manifest itself either by a failure of the regular initialization with`yagna payment init -r` or through an error you'll receive when running `yagna payment status`.

_Solution:_ In such a case, we're providing you with a fallback to normal payments, using our ERC-20 on-chain payment driver.

To enable it, first **stop and re-start the yagna daemon** and then run:

```text
yagna payment init -r --driver=ngnt
yagna payment status --platform=NGNT
```

After you confirm you have the funds, proceed with running the examples or your own requestor agent code normally. The providers are configured to accept both zkSync and the regular tokens and will adjust accordingly.

Once you finish a task run and should you verify the payments, remember to use [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io/) instead of the zkSync explorer.

