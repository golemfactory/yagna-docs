---
description: List of actions needed to execute the yacat example.
---

# Tutorial steps

## Let's get to work. Dockerfile

{% hint style="info" %}
\[czy to wszystko jest info?\]This tutorial is aimed to teach you how to create your own application on Golem. You can work with your own code or use yacat - ready made example.

yacat is made of two files:

* `yacat.Dockerfile` - the docker file used for provider's container images definition
* `yacat.py` - entry point. Orchestration of the containers.

Those files can be found in `/examples/yacat`directory of  [https://github.com/golemfactory/yapapi/tree/b0.3](https://github.com/golemfactory/yapapi/tree/b0.3) \[TODO - podac komende - w jakim katalogu uruchamiac\]
{% endhint %}

Let's start with Dockerfile. We would need a dedicated one, to have [Hashcat](https://hashcat.net/hashcat/) being executed in the containers. \[po co to jest - bo moze ktos nie wie - czy to jest "standard" czy ddykowany i co musi zrobic czlowiek jak bedzie oribl swoja appke\]

\[jakich elementow potrzeba zeby zrobic apke na golema\]

```text
FROM golemfactory/base:1.5

MAINTAINER Radek Tereszczuk <radoslaw.tereszczuk@golem.network>

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

VOLUME /golem/work /golem/output /golem/resource
```

This is pretty standard Dockerfile. The main take away is: \[musi by wiadomo ze rozpisuje powyzsze\]

```text
VOLUME /golem/work /golem/output /golem/resource
```

This makes `/golem/work` a place we will use for in / out file transfer. We are defining other volumes for possible future usage also.

We proceed with the `yacat.Dockerfile` with a standard docker build:

```python
docker build . -f yacat.Dockerfile -t yacat
```

As Golem Network can not use raw docker images and need to use `gvmkit` image format, we need to convert the docker image to Golem \(`gvmkit`\) image. This will be done by:

```python
pip install gvmkit-build
gvmkit-build yacat
gvmkit-build yacat --push
```

The important fact is that in the end, int the console out, we are getting the `gvmkit` image hash, that looks like this:

```python
2c17589f1651baff9b82aa431850e296455777be265c2c5446c902e9
```

This hash will identify our image when our application will run.

The details of docker image conversion are described here:

