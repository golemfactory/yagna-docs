---
description: Requestor agent mainnet configuration
---

# Running a requestor on Mainnet

{% hint style="info" %}
In order for the below commands and code to work, your `yagna` daemon must have the mainnet accounts correctly initialized using the instructions above.
{% endhint %}

After you have taken care of the above, the one last thing that you'll need to do if you want to request tasks from the providers running on the mainnet is enabling the mainnet driver in your requestor agent.

The examples we bundle with our APIs (the Blender rendering and Hashcat password recovery) expose two command-line arguments, analogous to yagna daemon itself: `--payment-driver` and `--payment-network`.

While the driver is `erc20` in both cases, the network does differ. 

Therefore, in order to run our examples on mainnet, you'd launch them using e.g.:

{% tabs %}
{% tab title="Python" %}
```
python3 blender.py --payment-network=mainnet
```
{% endtab %}

{% tab title="JS" %}
```
yarn js:blender --payment-network mainnet
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
    subnet_tag="public",
)
```
{% endtab %}

{% tab title="JS" %}
```javascript
new Executor({
    driver: "erc20",
    network: "polygon",
    subnet_tag: "public",
})
```
{% endtab %}
{% endtabs %}
