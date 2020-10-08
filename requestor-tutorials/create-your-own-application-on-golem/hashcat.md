---
description: How hashcat works and how to make it work in parallel
---

# Hashcat

## What is hashcat?

The [_Hashcat_](https://hashcat.net/hashcat/) __is a command-line utility that finds unknown passwords by its hash that is known.

{% hint style="info" %}
The [_Hashcat_](https://hashcat.net/hashcat/) __is a very powerful tool. It supports 320 hashing algorithms and 5 different attack types. We will use only phpass algorithm and a simple brute attack.
{% endhint %}

 First, we need to precisely define the "finding password" problem. Let's assume we have hash made by processing an unknown password by phpass algorithm. 

{% hint style="info" %}
Phpass is used as a hashing method by WordPress and Drupal. It is a public domain software and used with PHP applications.
{% endhint %}

The password hash is stored in in.hash file

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/
```

We assume we know that the password mask is:

```text
?a?a?a
```

That means that the password is made of 3 alpha characters.

Now we can try to find the password matching the given hash and mask, by calling:

```text
./hashcat -a 3 -m 400 in.hash ?a?a?a
```

The parameters used mean:

* `a 3` - use brute force type of attack. There are 5 other types of attacks.
* `m 400` - password is hashed witch the usage of phpass algorithm. There are 320 others.
* `in.hash` - name of a file containing the hashed password
* `?a?a?a` - mask to use

{% hint style="info" %}
The complete hashcat parameters reference is available here: [https://hashcat.net/wiki/doku.php?id=hashcat](https://hashcat.net/wiki/doku.php?id=hashcat) 
{% endhint %}

As a result of the above call, the `hashcat.potfile` will be created with the following content:

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/:pas
```

where `pas` is the password that was unknown to us. It has been cracked by the cat. 

{% hint style="info" %}
For longer passwords usage of hashcat might be a bit problematic as it might need a lot of processing time \(days, months\) to find passwords.
{% endhint %}

In order to crack long passwords faster, we created Golem Network version of Hashcat. It that will use the computing power of many providers at the same time. Parallel password finding is much quicker: Golem version will possibly run in hours and not days / months as the classic one.

## Doings things in parallel

\[nie jest zrozumiale\] \[dodac obrazek\] czy to jest dla hashcata czy dla tutoriala ?

How to make hash cat work in parallel? The answer is very simple: the keyspace concept. We can ask the cat to tell us what is the size of the possibility space for the given mask and algorithm:

```text
hashcat --keyspace -a 3 ?a?a?a -m 400
```

as a result, we will have an answer in the `stdout`. In our case it is `9025`.

Now we can divide the `0..9025` space into separate parts. Assuming we want to use 3 providers, those parts would be:

* `0..3008`
* `3009..6016`
* `6017..9025`

To process the exact part of the whole `0..9025` space, we use the following hashcat options:

```text
./hashcat -a 3 -m 400 in.hash --skip 3009 --limit 6016  ?a?a?a
```

The above call will process the `3009..6016` part. If there is any result in that range it will be written to the `hashcat.potfile`.

Now we just need to:

* provide each docker container with `in.hash` file \(the same for all providers\)
* execute `hashcat` with proper `--skip` / `--limit` values in each docker container
* transfer `hashcat.potfile` from each docker container to the requestor
* check if any of the potfiles contains password. If yes, present it to the user.

