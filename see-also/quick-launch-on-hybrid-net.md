---
description: A guide to help you run the yagna daemon with Hybrid Net feature enabled.
---

# Quick launch on Hybrid net

### Installation

We have enabled providers and requestors to run their nodes with the Hybrid Net feature.
You are very welcome to try it out!
Experimental Golem Network implementation provides better network scalability as well as increased performance with quicker responses and faster data transfers.

#### Provider
Open your terminal and type:

```
curl -ksSf https://join.golem.network/as-provider | YA_INSTALLER_CORE=pre-rel-v0.11.0 YA_INSTALLER_VM=v0.2.13 bash -
```

for further details regarding simple Provider node setup please follow [Becoming a provider](https://handbook.golem.network/provider-tutorials/provider-tutorial#initial-setup) tutorial.

#### Requestor
Open your terminal and type:

```
curl -ksSf https://join.golem.network/as-requestor | YA_INSTALLER_CORE=pre-rel-v0.11.0 bash -
```

for further details regarding simple Requestor setup please follow [Requestor development](https://handbook.golem.network/requestor-tutorials/flash-tutorial-of-requestor-development#confirm-the-installed-daemons-version) tutorial.

### Running the daemon

#### Provider

You can simply run Golem provider on Hybrid Net by typing the following in the terminal:
```
golemsp run
```

{% hint style="warning" %}
Important: Be aware that the default subnet for Provider running on Hybrid Net is `hybrid-mainnet`.
{% endhint %}

#### Requestor

You can start the daemon as you usually do:
```
yagna service run
```
After you launch the daemon, leave it running in the background. Remember to use `hybrid-mainnet` when running your tasks on Golem with the Hybrid Net feature enabled.

{% hint style="info" %}
This experimental Golem Network implementation is ready for your beta tests!
In order to run your tasks on Golem devnet you can try to reach out to the `hybrid` subnet but please remember that we're still under optimization and our testnet might occasionally be unstable.
{% endhint %}

### Port forwarding

In order to experience all the available functionalities, it is beneficial to have a public IP. This is required whether you are a Provider or Requestor.
Golem can't automatically configure your router to open port `11500`, therefore you will need to manually set it up.
For router specific instructions on how to forward your ports go to [https://portforward.com/](https://portforward.com/).
To check if your ports are forwarded correctly you can use [www.canyouseeme.org](http://www.canyouseeme.org/).

{% hint style="warning" %}
If port forwarding does not work, you may need to call your ISP to change settings on your router.
Don't worry if you are not able to acquire public IP nor open port. This is optional and won’t prevent you from using the Hybrid Net implementation.
{% endhint %}

### Can we help you? Do you have feedback for Golem?

{% hint style="success" %}
If you'd like to give us feedback and suggestions, if you have errors to report, or if you got stuck and need further help following our tutorials, please don't hesitate to reach out to us on our Golem Discord: [https://chat.golem.network](https://chat.golem.network)
{% endhint %}
