---
description: >-
  Example showing how to make REST call to an external public API from VM running on a Provider node.
---

# Service Example 6: External API Request

{% hint style="info" %}
The example depicts the following features:

* [Outbound Network](../vm-runtime/computation-payload-manifest.md#compmanifestnetinetout--object)
* [Computation Payload Manifest](../vm-runtime/computation-payload-manifest.md)
{% endhint %}

{% hint style="info" %}
Full code of the example is available in the yapapi repository: [https://github.com/golemfactory/yapapi/tree/master/examples/external-api-request](https://github.com/golemfactory/yapapi/tree/master/examples/external-api-request)
{% endhint %}

## Prerequisites

As with the other examples, we're assuming here you already have your [yagna daemon set-up to request the test tasks](../flash-tutorial-of-requestor-development/) and that you were able to [configure your Python environment](../flash-tutorial-of-requestor-development/run-first-task-on-golem.md) to run the examples using the latest version of `yapapi`. If this is your first time using Golem and yapapi, please first refer to the resources linked above.

This example involves [Computation Payload Manifest](../../requestor-tutorials/vm-runtime/computation-payload-manifest.md).

_Computation Payload Manifest_ making use of _Outbound Network_ requires either:

1. [Certificate](../../requestor-tutorials/vm-runtime/computation-payload-manifest.md#certificates) trusted by Providers
2. an instance of a Provider with domain this example will use added to its [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist)
3. an instance of a Provider with a self signed Certificate imported into its [keystore](../../provider-tutorials/provider-cli.md#keystore)

Following example will show cases 2. and 3. so it will be necesary to start a [local instance of a Provider](../../provider-tutorials/provider-tutorial.md).

## Example app

Example app will make a request to an external API using Provider's network and then it will print API response to the console.

### 1. Manifest file

In order for an app to make an _Outbound Network_ request it needs to declare which tools it will use and which URLs it will access in a [Computation Payload Manifest](../vm-runtime/computation-payload-manifest.md).

Our example will make a HTTPS request using `curl` to a public REST API with URL `https://api.coingecko.com`.

_Computation Payload Manifest_ will need to have following objects:

- [`net`](../vm-runtime/computation-payload-manifest.md#compmanifestnet--object) computation constraints with `URL`s the app will access (`https://api.coingecko.com`)
- [`script`](../vm-runtime/computation-payload-manifest.md#compmanifestscript) computation constraint with `command`s app will execute (`curl`)
- [`payload`](../vm-runtime/computation-payload-manifest.md#payload-object) defining [Golem image](../vm-runtime#preparing-a-vm-image) containing tools used by the app (`curl`)

Example _Computation Payload Manifest_ must follow a specific [schema](../vm-runtime/computation-payload-manifest.md#manifest-schema), and for our example it will take form of following `manifest.json` file:

```json
{
  "version": "0.1.0",
  "createdAt": "2022-07-26T12:51:00.000000Z",
  "expiresAt": "2100-01-01T00:01:00.000000Z",
  "metadata": {
    "name": "External API call example",
    "description": "Example manifest of a service making an outbound call to the external API",
    "version": "0.1.0"
  },
  "payload": [
    {
      "platform": {
        "arch": "x86_64",
        "os": "linux"
      },
      "urls": [
        "http://yacn2.dev.golem.network:8000/docker-golem-script-curl-latest-d75268e752.gvmi"
      ],
      "hash": "sha3:e5f5ddfd649525dbe25d93d9ed51d1bdd0849933d9a5720adb4b5810"
    }
  ],
  "compManifest": {
    "version": "0.1.0",
    "script": {
      "commands": [
        "run .*curl.*",
      ],
      "match": "regex"
    },
    "net": {
      "inet": {
        "out": {
          "protocols": ["https"],
          "urls": ["https://api.coingecko.com"]
        }
      }
    }
  }
}
```

Created file should be [verified using JSON schema](../vm-runtime/computation-payload-manifest.md#schema-verification).

Then it needs to be encoded in `base64`:

```sh
 base64 --wrap=0 manifest.json.base64 > manifest.json.base64
```
### 2. Yapapi example app

Base64 encoded _manifest_ can be configured using [`yapapi.payload.vm.manifest`](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function resulting in following `externa_api_request.py` file:

```py
import asyncio

from yapapi import Golem
from yapapi.services import Service
from yapapi.payload import vm

class OutboundNetworkService(Service):
    @staticmethod
    async def get_payload():
        return await vm.manifest(
            manifest = open("manifest.json.base64", "rb").read()
            # later we may add here manifest signature, digest algorithm, and app author's certificate
            min_mem_gib = 0.5,
            min_cpu_threads = 0.5,
            # capabilities used to reach Provider with a correct VM Runtime
            capabilities=["inet", "manifest-support"],
        )

    async def run(self):
        script = self._ctx.new_script()
        future_result = script.run(
            "/bin/sh",
            "-c",
            f"GOLEM_PRICE=`curl -X 'GET' \
                    'https://api.coingecko.com/api/v3/simple/price?ids=golem&vs_currencies=usd' \
                    -H 'accept: application/json' | jq .golem.usd`; \
                echo \"Golem price: $GOLEM_PRICE USD\";",
        )
        yield script

        result = (await future_result).stdout
        print(result.strip() if result else "")

async def main():
    async with Golem(budget=1.0, subnet_tag="testnet") as golem:
        await golem.run_service(OutboundNetworkService, num_instances=1)
        await asyncio.sleep(60)
```

### 3. Verification of a request with  Computation Payload Manifest

_Providers_ verify incoming request with a _Computation Payload Manifest_ by checking if it arrives with a [signature and _App author's certificate_ signed by a certificate they trust](../vm-runtime/computation-payload-manifest.md#certificates). If there is no signature they verify if URLs used by _Computation Payload Manifest_ are [whitelisted](../../provider-tutorials/provider-cli.md#domain-whitelist).

Thare are two ways to make our *local* _Provider_ to verify request:

- #### Whitelisting of domain used by the app

  Add `api.coingecko.com` to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist):

  `ya-provider whitelist add --patterns api.coingecko.com --type strict`

- #### Signing manifest and adding signature with a certificate to the request

  [Generate self signed certificate](../vm-runtime/computation-payload-manifest.md#self-signed-certificate-example) and then [generate manifest signature](../vm-runtime/computation-payload-manifest.md#manifest-signature).

  With generated and `base64` encoded certificate and a signature function `get_payload()` takes following form:

  ```py
  # ...
    async def get_payload():
        return await vm.manifest(
            manifest = open("manifest.json.base64", "rb").read(),
            manifest_sig = open("manifest.json.base64.sign.sha256.base64", "rb").read(),
            manifest_sig_algorithm = "sha256",
            manifest_cert = open("golem_requestor.cert.pem.base64", "rb").read(),
            min_mem_gib = 0.5,
            min_cpu_threads = 0.5,
            capabilities=["inet", "manifest-support"],
        )
  # ...
  ```

### 4. Launching the app

With both _Requestor_  and _Provider_ yagna nodes and `ya-provider` running in the backround run:

`python external_api_request.py`

(keep in mind to set `YAGNA_APPKEY` and `YAGNA_API_URL` env variables pointing to local _Requestor_ node)