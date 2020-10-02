---
description: Your own thing on golem.
---

# Create your own application on golem

## Introduction

The use case for the Golem network is to be used by developers to create their own applications on Golem. The Golem platform and the Golem SDK are carefully crafted for this scenario.

This tutorial shows typical own application development with the Golem port of [Hashcat](https://hashcat.net/hashcat/) open source password cracking tool.

## Prerequisites

* Supported operating system
  * OS X 10.14+
  * Ubuntu 18.04 or 20.04
  * Windows 10
* Python 3.6+, git and yagna daemon installed, as described in 

{% page-ref page="../requestor-tutorials-1/flash-tutorial-of-requestor-development.md" %}

* Being familiar with Requestor and Provider concepts. Those are described here:

{% page-ref page="../introduction/requestor.md" %}

{% page-ref page="../introduction/provider.md" %}

* Your own idea that maps to the map-reduce model and can be implemented as running multiple docker images on golem providers. 

_Initially, you can start just by experimenting with our example yacat - Golem_ [_Hashcat_](https://hashcat.net/hashcat/) _port._

## How does it work?

Currently, Golem network supports the following application architecture:

* Application is divided into two parts:
  * **Requestor** \(sometimes called _a_ _master node_\). Divides the computation problem into several parts, and send them to providers. After receiving all the results from the providers, the requestor combines them to form the final output that is passed to the user.
  * **Provider** \(sometimes called _worker node_\). Executes the given part and returns results to the requestor.
* The Provider side execution is implemented as the docker container.
* The application creator prepares a dedicated dockerfile that describes the image. 
  * _If there \(for example on the docker hub\) exist image that can be used directly, there is no need to create a custom image._
* The application starting point is the Requestor side, which runs the requestor agent.
* The requestor agent gets the providers that meet its needs from the market.
* The providers are asked to load the appropriate image. 
  * _If this is a subsequent run of the requestor, the image could already be cached by some of the providers._ 
* For each of the providers, the requestor prepared input data. Those are sent from the memory or local requestor's file system into the docker container's file system.
* One or several commands are executed on the provider's docker containers.
  * _It is expected that in the result of the command execution, in the docker container's file system there are some files that can be transferred to the requestor._
* Requestor transfers needed files from the provider's docker container's file systems.
* Requestor combines all the data from providers to form final output that can be consumed by the application user.

![](../.gitbook/assets/tnm-docs-infographics-06.jpg)

Some additional details can be found here:

{% page-ref page="../introduction/golems-details.md" %}

## Let's get to work. Dockerfile

Let's start with Dockerfile. We would need a dedicated one, to have [Hashcat](https://hashcat.net/hashcat/) ready to be used.

```text
FROM golemfactory/base:1.5

MAINTAINER Radek Tereszczuk <radoslaw.tereszczuk@golem.network>

RUN apt update

RUN apt-get update && apt-get install -y alien clinfo

# Install Intel OpenCL driver
#ENV INTEL_OPENCL_URL=http://registrationcenter-download.intel.com/akdlm/irc_nas/vcp/13793/l_opencl_p_18.1.0.013.tgz
ENV INTEL_OPENCL_URL=http://registrationcenter-download.intel.com/akdlm/irc_nas/9019/opencl_runtime_16.1.1_x64_ubuntu_6.4.0.25.tgz

RUN mkdir -p /tmp/opencl-driver-intel
WORKDIR /tmp/opencl-driver-intel
RUN curl -O $INTEL_OPENCL_URL; \
    tar -xzf $(basename $INTEL_OPENCL_URL); \
    for i in $(basename $INTEL_OPENCL_URL .tgz)/rpm/*.rpm; do alien --to-deb $i; done; \
    dpkg -i *.deb; \
    mkdir -p /etc/OpenCL/vendors; \
    echo /opt/intel/*/lib64/libintelocl.so > /etc/OpenCL/vendors/intel.icd; \
    rm -rf *

ENV HASHCAT_VERSION        hashcat-5.1.0
ENV HASHCAT_UTILS_VERSION  1.9

# Update & install packages for installing hashcat
RUN apt-get update && \
    apt-get install -y wget p7zip make build-essential git libcurl4-openssl-dev libssl-dev zlib1g-dev

RUN mkdir /golem/yacat

WORKDIR /golem/yacat
RUN wget --no-check-certificate https://hashcat.net/files/${HASHCAT_VERSION}.7z && \
    7zr x ${HASHCAT_VERSION}.7z && \
    rm ${HASHCAT_VERSION}.7z

RUN wget --no-check-certificate https://github.com/hashcat/hashcat-utils/releases/download/v${HASHCAT_UTILS_VERSION}/hashcat-utils-${HASHCAT_UTILS_VERSION}.7z && \
    7zr x hashcat-utils-${HASHCAT_UTILS_VERSION}.7z && \
    rm hashcat-utils-${HASHCAT_UTILS_VERSION}.7z

#Add link for binary
RUN ln -s /golem/yacat/${HASHCAT_VERSION}/hashcat64.bin /usr/bin/hashcat
RUN ln -s /golem/yacat/hashcat-utils-${HASHCAT_UTILS_VERSION}/bin/cap2hccapx.bin /usr/bin/cap2hccapx

RUN cp /golem/yacat/${HASHCAT_VERSION}/hashcat.hcstat2 /golem/yacat
RUN chmod -R 777 /golem/yacat

RUN apt clean

WORKDIR /golem/work

VOLUME /golem/work
```

This is pretty standard Dockerfile. The main takeaways are:

* The `/golem/work` is our working directory. This is done by

```text
WORKDIR /golem/work
```

* We also need to define a dedicated volume for the `/golem/work`

```text
VOLUME /golem/work
```

This makes `/golem/work` a place we will use for in / out file transfer.

## The work to do

The [_Hashcat_](https://hashcat.net/hashcat/) __is a very powerful tool. To make our example simple, we will use it in a very basic manner.

Let's assume we have hash made by processing an unknown password by phpass algorithm.

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

* `a 3` - use brute force type of attack
* `m 400` - password is hashed witch usage of phpass algorithm
* `in.hash` - name of a file containing the hashed password
* `?a?a?a` - mask to use

{% hint style="info" %}
The complete hashcat parameters reference is aviaible here: [https://hashcat.net/wiki/doku.php?id=hashcat](https://hashcat.net/wiki/doku.php?id=hashcat) 
{% endhint %}

As a result of the above call, the `hashcat.potfile` will be created with the following content:

```text
$P$5ZDzPE45CLLhEx/72qt3NehVzwN2Ry/:pas
```

where `pas` is the password that was unknown to us and has been cracked by the cat. 

## Doings things in parallel

How to make hash cat work in parallel? The answer is very simple: the keyspace concept. We can ask the cat to tell us what is the size of the possibility space for given mask and alghorithm:

```text
hashcat --keyspace -a 3 ?a?a?a -m 400
```

as a result, we will have an answer in the stdout. In our case it is `9025`.

Now we can divide the `0..9025` space into separate parts. Assuming we want to use 3 providers, those parts would be:

* `0..3008`
* `3009..6016`
* `6017..9025`

To process the exact part of the whole `0..9025` space, we use following hashcat options:

```text
./hashcat -a 3 -m 400 in.hash --skip 3009 --limit 6016  ?a?a?a
```

The above call will process the `3009..6016t` part. If there is any result in that range it will be written to the `hashcat.potfile`.

Now we just need to:

provide each docker container with `in.hash` file \(the same for all providers\)

 execute  command that uses proper skip / limit values in each docker.

