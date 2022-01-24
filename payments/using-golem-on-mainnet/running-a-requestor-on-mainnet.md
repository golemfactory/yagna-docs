---
description: Requestor agent mainnet configuration
---

# Running a requestor on Mainnet

{% hint style="info" %}
In order for the below commands and code to work, your `yagna` daemon must have the mainnet accounts correctly initialized using the instructions above.
{% endhint %}

After you have taken care of the above, the one last thing that you'll need to do if you want to request tasks from the providers running on the mainnet is enabling the mainnet driver in your requestor agent.

The examples we bundle with our APIs (the Blender rendering and Hashcat password recovery) expose two command-line arguments, analogous to yagna daemon itself: `--driver` and `--network`.

{% hint style="danger" %}
There is a an additional caveat here though.

In order to clearly separate our production network, to which the majority of the provider nodes run by our users connect by default, from the testnet subnet the sole purpose of which should be testing your apps, we have introduced a concept of a "subnet tag".

Whereas the limited number of our own test providers that we make available to our prospective requestors use the `devnet-beta` subnet (which is included by default in our requestor-facing examples), the mainnet providers use `public-beta` subnet by default.

Thus, to leverage the computing power of the mainnet providers in the Golem network, you must provide the subnet tag used by those mainnet provider nodes - `public-beta`.
{% endhint %}

Therefore, combining those parameters, in order to run our examples on mainnet, you'd launch them using e.g.:

{% tabs %}
{% tab title="Python" %}
```
python3 blender.py --payment-network=mainnet --subnet-tag=public-beta
```
{% endtab %}

{% tab title="JS" %}
```
yarn js:blender --payment-network mainnet --subnet-tag public-beta
```
{% endtab %}
{% endtabs %}

### Requestor agent code

As for your own requestor agent code, you'll need to supply the appropriate `payment_driver` , `payment_network` and `subnet_tag` parameters to `Golem`.

{% tabs %}
{% tab title="Python" %}
```python
async with Golem(
    [...],
    payment_network="polygon",
    payment_driver="erc20",
    subnet_tag="public-beta",
)
```
{% endtab %}

{% tab title="JS" %}
```javascript
new Executor({
    driver: "erc20",
    network: "polygon",
    subnet_tag: "public-beta",
})
```
{% endtab %}
{% endtabs %}
