---
description: Symptoms and solutions of known issues.
---

# Common issues

### No access to VM

_**Description:**_ No access to VM

 _**Solution:**_ `curl -o setup-kvm.sh https://join.golem.network/setup-kvm.sh && chmod +x ./setup-kvm.sh && ./setup-kvm.sh` 

Note: make sure `qemu-vm` is installed first with `apt install qemu-kvm`.

### IO error: No such file or directory

_**Os:**_ Any

_**Description:**_  Local service error: Transfer error: IO error: No such file or directory \(os error 2\)

_**Solution:**_  Something went wrong with the computation. Check that you're following the [Define your task's steps](https://handbook.golem.network/requestor-tutorials/requestor-tutorial#define-your-tasks-steps) correctly and that you remembered to define a place \(or places\) in the container file system that will be used for the file transfer, [as shown here](https://handbook.golem.network/requestor-tutorials/create-your-own-application-on-golem/the-steps-to-do#volume-the-input-output). 

With `ctx.run()`  make sure that you don't have multiple arguments in one string. Either `ctx.run("/bin/sh", "-c", "a", "b", "c" ...)` or use the syntax the [example gives](https://handbook.golem.network/requestor-tutorials/create-your-own-application-on-golem/the-steps-to-do#the-requestor-agent-code) where it parses in lines.

In the scenario that you're still stuck, you always have the option to investigate what is happening deeper by pulling the logs back instead of your output file. For example:

```text
commands = (
    f"somecommand input.file output.file >> /golem/output/log.txt 2>&1"
)

ctx.run("/bin/sh", "-c", commands)

ctx.download_file("/golem/output/log.txt", "log.txt")
#ctx.download_file("/golem/output/output.file", output_file)
```

### Symlink issues

_**Os:** Ubuntu_

_**Description:**_ If you run the Golem Provider one-line installer on a minimal install of Ubuntu and it completes without error but doesn't run then you might have a `symlink` issue.

_**Solution:** See_ [_this guide_](https://websiteforstudents.com/setup-and-manage-symlinks-on-ubuntu-18-04-16-04/) _on setting up and managing Simlinks._

### Connectivity issue

_**Os:** All_

_**Description:**_ When someone is not receiving tasks at all, has correct subnet configured, and VM valid, the most probable cause is yagna "connectivity" issue

_**Solution:**_ Kill and restart the process

### Payment driver initialization issue

_**Os:**_ All, requestor only

_**Description:**_ Since our newest addition to Golem - the integration with zkSync, layer 2 payment solution - is, so far, a highly experimental feature, it may still sometimes happen that the yagna daemon fails to initialize itself correctly.

This will manifest itself either by a failure of the regular initialization with`yagna payment init -r` or through an error you'll receive when running `yagna payment status`.

_**Solution:**_ In such a case, we're providing you with a fallback to normal payments, i.e. regular GLM token transfer on the Ethereum chain.

To enable it, first **stop and re-start the yagna daemon** and then run:

```text
yagna payment init -r --driver=ngnt
yagna payment status --platform=NGNT
```

After you confirm you have the funds, proceed with running the examples or your own requestor agent code normally. The providers are configured to accept both zkSync and the regular tokens and will adjust accordingly.

Just remember to use [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io/) instead of the zkSync explorer, should you wish to verify that the payment went through.

