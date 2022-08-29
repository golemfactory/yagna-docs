---
description: Guides to help you run the yagna daemon with hybrid net feature enabled.
---

# Quick launch on hybrid net

### Installation

We have enabled providers and requestors to run their nodes with hybrid net feature. You are very welcome to try it out! 

#### Provider
Open your terminal and type:

``` 
curl -ksSf https://join.golem.network/as-provider | YA_INSTALLER_CORE=pre-rel-v0.11.0 YA_INSTALLER_VM=pre-rel-v0.2.12-rc3 bash -
```

for further details regarding simple Provider node setup please follow [Becoming a provider](https://handbook.golem.network/provider-tutorials/provider-tutorial#initial-setup) tutorial.

#### Requestor
Open your terminal and type:

``` 
curl -ksSf https://join.golem.network/as-provider | YA_INSTALLER_CORE=pre-rel-v0.11.0 bash -
```

for further details regarding simple Requestor setup please follow [Requestor development](https://handbook.golem.network/requestor-tutorials/flash-tutorial-of-requestor-development#confirm-the-installed-daemons-version) tutorial.

### Running the daemon

#### Provider

To run the Golem provider on hybrid net, type the following in the terminal:
```
golemsp run --subnet hybrid-mainnet
```

#### Requestor

You can run the daemon as you usually do:
```
yagna service run
```

{% hint style="warning" %}
Important: After you launch the daemon, leave it running in the background. Remember to use `hybrid-mainnet` when running your tasks on Golem. 
{% endhint %}

### Can we help you? Do you have feedback for Golem?

{% hint style="success" %}
If you'd like to give us feedback, suggestions, have some errors to report or if you got stuck and need help while following our tutorials, please don't hesitate to reach out to us on our Golem Discord: [https://chat.golem.network](https://chat.golem.network)
{% endhint %}
