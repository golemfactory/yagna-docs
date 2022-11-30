---
description: A guide to help you run your node with the public IP address and port forwarding.
---

# Port forwarding

To help Golem Network grow and become more resilient and stable it needs more nodes with public IP addresses. This is
helpful whether you are running a Provider or Requestor node. Golem can't automatically configure your router to open
UDP port `11500`, therefore you will need to manually set it up. For router specific instructions on how to forward your
ports go to [https://portforward.com/](https://portforward.com/). To check if your ports are forwarded correctly you can
use [www.canyouseeme.org](http://www.canyouseeme.org/).

{% hint style="warning" %}
If port forwarding doesn't work, you may need to call your ISP to change settings on your router.
Don't worry if you are unable to acquire a public IP or open a port. This is optional and won’t prevent you from using
the New Network Driver implementation.
{% endhint %}
