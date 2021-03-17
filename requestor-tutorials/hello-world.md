---
description: 'Creating your first, simple app on Golem'
---

# Hello World from Golem

_This tutorial is the textual counterpart to a workshop originally prepared by Jakub Mazurek, a Software Developer at Golem Factory and presented during the Hello Decentralization conference in Feb, 2021._

Now that we've seen how easy it is to [run a Golem requestor agent](flash-tutorial-of-requestor-development.md), then had a look at [how this stuff works under the hood](requestor-tutorial.md) and finally learned how to go about [creating your own Golem VM application image](convert-a-docker-image-into-a-golem-image.md), we can put this knowledge to the test and build the most bare-bones Golem app.

{% hint style="info" %}
If you'd rather like to have a more general introduction on the idea behind Golem or would like to learn what components constitute a Golem node and the Golem network, please have a look at:

{% page-ref page="../introduction/golem-overview.md" %}

{% endpage-ref %}
{% endhint %}

## Step 0. What are we building?

The application we'll build and run on Golem will be a very simple, quick-and-dirty, **distributed hash cracker** implemented purely in Python that will perform a dictionary attack on a specific hash that we'd like to decipher.

{% hint style="info" %}
For the sake of clarity for those less versed with the terminology, a short explanation is due.

A [**dictionary attack**](https://en.wikipedia.org/wiki/Dictionary_attack) involves running some \(usually known\) hashing function on each word from some input dictionary in the hope that one of the resulting hashes will match the one that we're matching against. Getting a match means we have found the original plain text string that's hidden behind that hash.

The string might have been a password or some other secret that's usually stored only in an encrypted \(well, technically, hashed\) form to prevent someone who got into possession of such a string from being able to read the secret directly.

The only way to recover the original password then would be to perform a brute-force attack against such a hash, using _all_ possible character combinations up until some arbitrary character length. The caveat is that such attacks are usually - and by design - prohibitively expensive computation-time-wise.

Hence, an attacker may try a dictionary attack, constructing hashes out of a limited set of words, assuming that the person who defined the password used some regular word from a dictionary.
{% endhint %}

We'll use this idea mainly because it scales in a very straightforward manner - the input dictionary can be easily sliced and each slice sent to a different provider to be processed simultaneously. That makes it an excellent example of an application that leverages the most fundamental feature of Golem - the ability to distribute computational loads.

We chose it also because we can do it using Python's bundled modules, without depending on any external libraries \(apart from `yapapi` - [Golem's high-level API](https://github.com/golemfactory/yapapi) - and its dependencies in the requestor agent, of course\).

For your convenience, we're providing some boilerplate code in a Github repository created specifically for the purpose of the original workshop and our piece here:

{% embed url="https://github.com/golemfactory/hash-cracker" caption="" %}

{% embed url="https://www.docker.com/products/docker-desktop" caption="" %}

1. Our high-level API reference to help you on your way:
2. And in case you get stuck or need help, please reach out to us on our Discord chat and we'll be delighted to help you out :\)

{% embed url="https://chat.golem.network/" caption="" %}

**Have fun with Golem!**

