---
description: How hashcat works and how to make it work in parallel.
---

# Hashcat

## What is hashcat?

[_Hashcat_](https://hashcat.net/hashcat/) \_\_is a command-line utility that finds unknown passwords from their known hashes.

{% hint style="info" %}
[_Hashcat_](https://hashcat.net/hashcat/) \_\_is a very powerful tool. It supports 320 hashing algorithms and 5 different attack types. We will use only the "phpass" algorithm and a simple brute-force attack.
{% endhint %}

First, we need to precisely define the "finding a password" problem. Let's assume we have a hash obtained from processing of an unknown password using the "phpass" algorithm.

{% hint style="info" %}
Phpass is used as a hashing method by e.g. WordPress and Drupal. Those are free/open-source web frameworks used to run PHP-based websites.
{% endhint %}

The password hash is stored in `in.hash` file and the hash is:

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/
```

We're going to assume that we know the password mask. It is:

```text
?a?a?a
```

That means that the password consists of 3 alphanumeric characters.

Now we can try to find the password, matching the given hash and mask, by calling:

```text
./hashcat -a 3 -m 400 in.hash ?a?a?a
```

The parameters are:

* `a 3` - use a brute-force attack. There are 5 other types of attacks.
* `m 400` - password is hashed with the phpass algorithm. There are 320 others alghoritms supported by Hashcat.
* `in.hash` - name of a file containing the hashed password
* `?a?a?a` - mask to use

{% hint style="info" %}
The complete hashcat arguments reference is available here: [https://hashcat.net/wiki/doku.php?id=hashcat](https://hashcat.net/wiki/doku.php?id=hashcat)
{% endhint %}

As a result of the above call, the `hashcat.potfile` will be created with the following content:

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/:pas
```

where `pas` is the password which had been unknown to us and was just retrieved by hashcat.

{% hint style="info" %}
Obviously, for longer passwords, the presented usage of hashcat could be problematic as it would require a lot more processing time \(e.g. days or even months\) to find a password with such a naive method.
{% endhint %}

To showcase how a similar problem can be resolved faster, we created the Golem version of Hashcat. It uses the computing power of many providers at the same time. Parallellized password recovery can be much quicker - instead of days or moths, this Golem version is likely to solve the problem in hours.

## Doings things in parallel

How to make Hashcat work in parallel? The answer is quite simple: the keyspace concept. We can ask the tool to tell us what the size of the possibility space \(keyspace\) is for the given mask and algorithm:

```text
hashcat --keyspace -a 3 ?a?a?a -m 400
```

As a result, we will receive an answer in the standard output. In our case it is `9025`.

Now we can divide the `0..9025` space into separate fragments. Assuming we want to allow our app to use up to 3 separate workers \(which means up to 3 providers\), those parts would be:

* `0..3008`
* `3009..6016`
* `6017..9025`

To process only the part of the whole `0..9025` space, we use the `--skip` and `--limit` options:

```text
./hashcat -a 3 -m 400 in.hash --skip 3009 --limit 6016  ?a?a?a
```

The above call will process the `3009..6016` part. If there is any result in that range it will be written to the `hashcat.potfile`.

## How to use hashcat in Golem?

* provide each running Docker container with `in.hash` file \(the same for all fragments\)
* execute `hashcat` with proper `--skip` / `--limit` values in each Docker container
* transfer `hashcat.potfile` from each Docker container to the requestor
* check if any of the resultant potfiles contains a password. If yes, present it to the user.

