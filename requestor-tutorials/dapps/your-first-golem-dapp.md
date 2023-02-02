---
description: >-
  On this page, you can discover how to deploy a decentralized app (dApp) on
  Golem with a single compose file.
---

# Your first Golem dApp

## Available experiments

While working with dApps, we created a few applications on top of it, which served us both as a testing ground and as a way to validate our approach. On the other hand, they were also designed to give you a good starting point or serve as reference when developing your own, similar apps.

### ToDo List Application [\[GitHub\]](https://github.com/golemfactory/dapp-experiments/tree/main/01\_todo\_app)

![ToDo List App](https://user-images.githubusercontent.com/5244214/201047967-f42dea7d-3e19-488b-9900-375f19badd96.png)

This application showcases utilizing the Golem Network to host a 3-layer application (**React** + **Flask** + **RQLite**)

### Weather Stats Application [\[GitHub\]](https://github.com/golemfactory/dapp-experiments/tree/main/weather\_stats)

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Weather Stats App</p></figcaption></figure>

This application presents usage of the Golem Network with access to external services (not hosted on Golem) taking advantage of the outbound network connections.

## Pre-installation

To launch dApps on Golem, you request computation resources from the network - therefore, you need the following prerequisites prior to execution:

* a running Yagna Daemon (v0.12 or higher)
* available AppKey

Setting these up is a part of the tutorial below. You can move on to the next section once you have these prerequisites ready.

{% content-ref url="flash-tutorial-of-requestor-development/" %}
[flash-tutorial-of-requestor-development](flash-tutorial-of-requestor-development/)
{% endcontent-ref %}

## Installation

The tool which deploys apps to Golem, `dapp-runner` is installable from the PyPi repository with the following command:

```shell
pip install -U pip
pip install dapp-runner
```

### Installation from sources

Alternatively, if you'd like to have the latest package, you can install it from the source. \
To do so, clone the repository from GitHub first:

```
git clone --recurse-submodules https://github.com/golemfactory/dapp-runner.git
```

Next, enter the newly created directory and install the tool using the following commands:

```shell
cd dapp-runner
pip install -U pip poetry
poetry install
```

For more information on the installation process, [visit the repository page](https://github.com/golemfactory/dapp-runner#quick-start)

## Running dApp on Golem

Having the above setup complete, you can verify it by running a sample application that comes together with `dapp-runner` repository using the following commands:

```shell
YAGNA_APPKEY=<your_key> dapp-runner start --config configs/default.yaml dapp-store/apps/webapp.yaml
```

The app will begin deployment, and you should finally see a log entry similar to the one below:

```json
{"http": {"local_proxy_address": "http://localhost:8080"}}
```

This means that the app is ready and can be viewed at: [http://localhost:8080](http://localhost:8080)

### Config files

Taking the ToDo List app as an example, it was originally written without any Golem context in mind,
with full dockerization and docker-compose support. The only Golem-specific files added were:

* **`golem-compose.yml`** to define the application-specific Golem config (image hashes, capabilities, init commands)
* **`golem-config.yml`** to define the runtime-specific Golem config (yagna appkey, subnet, budget)

Having these two files ready, you can run an application on Golem with the following command 
(substituting `<your_key>` with an actual key you've obtained in the setup section):

```
YAGNA_APPKEY=<your_key> dapp-runner start --config golem-config.yml golem-compose.yml
```

After running this command, besides debug logs, you should look for the following entries:

```
Starting app: ToDo List App

{"db": {"0": "pending"}}
{"db": {"0": "starting"}}
{"db": {"0": "running"}}
{"db": {"0": "running"}, "api": {"0": "pending"}}
{"db": {"0": "running"}, "api": {"0": "starting"}}
{"db": {"0": "running"}, "api": {"0": "running"}}
{"db": {"0": "running"}, "api": {"0": "running"}, "web": {"0": "pending"}}
{"db": {"0": "running"}, "api": {"0": "running"}, "web": {"0": "starting"}}
{"db": {"0": "running"}, "api": {"0": "running"}, "web": {"0": "running"}}

[2022-11-10T10:52:39.306+0100 INFO dapp_runner.runner] Application started.
{"web": {"local_proxy_address": "http://localhost:8081"}}
```

To see the app in action, follow the link provided in `local_proxy_address` variable (with the port being dynamically assigned).

### Development

If you'd like to modify this app or create your own, the development flow doesn't change that much from regular web app development, with the exception of a few additional steps that we mention in the later part of this document.

At the moment, **starting Golem deployment requires you to have Docker images ready for your project**. The only way of creating GVMI (an image that Golem uses) is by providing a Docker image for conversion.

If you'd like to know more about the GVMI images and about the conversion process, please refer to:

{% content-ref url="vm-runtime/" %}
[vm-runtime](vm-runtime/)
{% endcontent-ref %}

In the following sections, we'll take the "ToDo List" app as an example of what the development process looks like. Even though the names of the images/services may change, other things will stay mostly the same

#### Deploying on Golem

Once you're satisfied with the code or changes you've made, the next thing is to deploy your app on Golem. There are a few steps to be followed to do so:

* Build containers with Docker Compose
* Create GVMI images from docker images
* Update the `golem-compose.yml` definition with the updated hashes (or create a new one)

**If you have only changed one component (only one image has changed), please remember to build and convert only parts related to it - GVMI images based on the same docker container will fail to upload.**

Starting with the Docker containers, create new images with the following command:

```
$ docker compose build api web
```

This will result in new docker images called `todo-app-api:latest` and `todo-app-web:latest`. 
These two images will be used to receive GVMI hashes to be used with `golem-compose.yml`. 
The process will be the same, only the image name will be different:

```
# build api
$ gvmkit-build todo-app-api:latest

# upload api
$ gvmkit-build todo-app-api:latest --push

# After upload is complete, please take the api hash value after log with "hash link:"


# build webapp
$ gvmkit-build todo-app-web:latest

# upload webapp
$ gvmkit-build todo-app-web:latest --push

# After upload is complete, please take the web hash value after log with "hash link:"
```

Having both of these hashes, please open the `golem-compose.yml` file and update the `payloads` definition with the updated hashes:

```diff
payloads:
  db:
    runtime: "vm"
    params:
      image_hash: "85021afecf51687ecae8bdc21e10f3b11b82d2e3b169ba44e177340c"
  api:
    runtime: "vm"
    params:
-      image_hash: "7df11ba76dc45f3a36d7c0a2efe318abb05384869b45b260471f4be7"
+      image_hash: "<api_hash>"
  web:
    runtime: "vm"
    params:
-      image_hash: "eb67411fe5e48ee56c6172ebe4cf2a0aa7c80a62dae781fe0d524649"
+      image_hash: "<web_hash>"
```

Now, the updated app can be started with:

```
YAGNA_APPKEY=<your_key> dapp-runner start --config golem-config.yml golem-compose.yml
```

If you'd like to see the full files, see [golem-compose.yml](https://github.com/golemfactory/dapp-experiments/blob/main/01\_todo\_app/golem-compose.yml) and [golem-config.yml](https://github.com/golemfactory/dapp-experiments/blob/main/01\_todo\_app/golem-config.yml) on GitHub.

