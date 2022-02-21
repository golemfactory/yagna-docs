# FAQ

**Can I run services (webservers, nodejs etc.) on Golem?**

Yes but in a limited way, meaning that you could use the network as a proxy for computing the response locally on the providers and then using your requestor as a loadbalancer that takes in request, and forwards the responses from the providers to the end user. \
\
Here's an example of such setup.  [https://github.com/golemfactory/yapapi/tree/master/examples/http-proxy](https://github.com/golemfactory/yapapi/tree/master/examples/http-proxy)

We're aiming to add support for simple web applications later in 2022.

**When do I start receiving tasks?**

It’s hard to say as it depends on a lot of factors since Golem is a marketplace. So the hardware you’re offering has to be demanded and secondly pricing is probably the most important factor also. If you don’t receive any tasks, try reducing your price. To get a feeling of other peoples pricing with similar specs, you can use the stats page at [https://stats.golem.network](https://stats.golem.network)\
\
A great start is to follow or undercut the median pricing of the network, which you can find under the **Provider > Pricing Analytics** tab

**Do I need to portforward to run golem?**\
No it’s not required.

**Can I run multiple providers on the same IP?**&#x20;

Yes, that works perfectly fine.

**Can I change price while executing tasks ?**

You can always change the pricing of your node, but it won't affect the current agreements that you've settled with a requestor. It only affect future ones.

**Where can I find information about Golem Community Incentives Program (CIP)** :thumbsup:****

{% embed url="https://blog.golemproject.net/community-incentives-program" %}

**Is there any stats for the network?**

Yes, you can check out : [https://stats.golem.network/](https://stats.golem.network)

**Can I combine multiple machines into one provider?**\
No you can not do that. You can setup multiple providers though.

**How does CPU/h pricing work?**\
CPU/h is pricing per utilization of a core. So if a requestor is using 4 cores and you have a CPU/h pricing of 0.1 GLM, then it would cost the requestor 0.4 GLM to use those 4 cores for an hour.\
\
**How are providers selected to compute a task?**\
If your node meets the requirements of the requestors demand, then it’s randomly selected along with other nodes on the network.

**What hardware requirements are there to run a provider?**\
None defined actually. Golem accepts everything as long as it’s a 64bit x86-64 CPU.

**What is Layer 1 and Layer 2 ?**

Here's a very very simplified explanation: Layer 1 is the most upper layer in the blockchain which contains all information in transactions. Layer 2 solutions are further down and doesn't include as much information and thus its cheaper to send transactions because you don't include as much info on the blockchain compared to Layer 1.

**What is tGLM and GLM :**

tGLM – test currency that you can obtain for free to test your requestor node. These tokens have no real value.

GLM – real currency that can be exchanged for cash

**Does Golem automatically clean task data?**

Yes, Golem cleans the task data directories via a default schedule of 30 days. However you can configure this schedule yourself via `ya-provider clean –help`

**Who are the top requestors on this network?**

At this current stage the daemon doesn't collect many metrics related to requestors. Metrics related to the requestors demand are not collected, but instead metrics like how many tasks and payment amounts are collected.

**Can I run golem on popular hosting services like OVH/AWS ?**

It all comes down to if KVM access are available on the hosting platform (e.g AWS doesn’t support KVM, while OVH cloud does)

**Where do I find yagna logs :**

`$HOME/.local/share/yagna/yagna_rCURRENT.log`

`$HOME/.local/share/ya-provider/yagna_rCURRENT.log`

**Would a provider Windows version be coming anytime soon?**

We have no specified target date but we are actively exploring adding support for it.

**Is golem a ERC-20 token and what’s a ERC-20 ?**

Yes, golem is an ERC-20 token.

**Why do people run nodes on the testing network ?**

Most common reason is to support requestors in testing their applications for free, so they quicker can progress with migrating their application to mainnet.

**What’s KVM ?**

KVM (Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86/x64 hardware containing virtualization extensions (Intel VT or AMD-V).

Golem uses this module to create a VM that tasks on the provider are computed inside.

**How do I update golem to the newest version ?**

Shutdown provider and run the installer again : `curl -sSf https://join.golem.network/as-provider | bash -`
