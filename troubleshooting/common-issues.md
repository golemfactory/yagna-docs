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

