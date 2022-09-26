---
description: Computation Payload Manifest description, its schema, and configuration guide
---

# Computation Payload Manifest

_Computation Payload Manifest_ allows [Requestor](../../introduction/requestor.md) to define application package _Payload_ and allows to set constraints on _Computations_ performed on [Provider](../../introduction/provider.md) node.

Request with a manifest can be [configured in yapapi](#configuration). 

Provider node operator controls what work can be performed by:

  - Importing public certificates of trusted authors of applications to Provider's [keystore](../../provider-tutorials/provider-cli.md#keystore) (which allows to verify _manifest_ [signature](#certificate-and-signature))

  - Adding domain patterns to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist) (which makes [signature](#certificate-and-signature) optional for some _manifests_)

## Configuration

Manifest can be configured as a [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function parameter together [manifest signature and app author's certificate](#certificate-and-signature) (which is sometimes required).

Example configuration:

Prepare `manifest.json` which follows [Computation Payload Manifest shema](#manifest-schema). Then encode it in base 64:

```sh
 base64 --wrap=0 manifest.json.base64 > manifest.json.base64
```

Sign it with your private key using e.g `sha256` digest algorithm.
Then encode both signature and your certificate (DER or PEM or PEM certificates chain) in base64:

```sh
openssl dgst -sha256 -sign my.private.key -out manifest.json.base64.sign.sha256 manifest.json.base64
base64 manifest.json.base64.sign.sha256 --wrap=0 > manifest.json.base64.sign.sha256.base64
base64 certificate.der --wrap=0 > certificate.der.base64
```

Then configure it all using `yapapi.payload.vm.manifest` function:

```py
import asyncio

from yapapi import Golem
from yapapi.services import Service
from yapapi.payload import vm

class OutboundNetworkService(Service):
    @staticmethod
    async def get_payload():
        manifest = open("manifest.json.base64", "rb").read()

        manifest_sig = open("manifest.json.base64.sign.sha256.base64", "rb").read()

        manifest_sig_algorithm = "sha256"

        # both DER and PEM formats are supported
        manifest_cert = open("requestor.cert.der.base64", "rb").read()

        return await vm.manifest(
            manifest=manifest,
            manifest_sig=manifest_sig,
            manifest_sig_algorithm=manifest_sig_algorithm,
            manifest_cert=manifest_cert,
            min_mem_gib=0.5,
            min_cpu_threads=0.5,
            capabilities=["inet", "manifest-support"],
        )

    async def run(self):
        script = self._ctx.new_script()
        future_result = script.run(
            "/bin/sh",
            "-c",
            f"API_OUT=`curl -X 'GET' 'https://api.some-public-service.com'`; \
                echo \"API request output: $API_OUT\";",
        )
        yield script

        result = (await future_result).stdout
        print(result.strip() if result else "")


async def main():
    async with Golem(budget=1.0, subnet_tag="devnet-beta") as golem:
        await golem.run_service(OutboundNetworkService, num_instances=1)
        await asyncio.sleep(30)
```

## Manifest schema

<!-- 
Schema generated using: https://github.com/golemfactory/yagna/blob/2088-computation-payload-manifest-schema/utils/manifest-utils/README.md#computation-payload-manifest-schema
Schema doc generated using: https://github.com/CesiumGS/wetzel 
cmd: wetzel computation-payload-manifest.schema.json -w -p computation-payload-manifest.schema.json -s computation-payload-manifest.schema.md > computation-payload-manifest.schema.md
 -->
_Computation Payload Manifest_ must follow a specific [JSON Schema](computation-payload-manifest.schema.json) ([Documentation](computation-payload-manifest.schema.md))

Manifest can be verified using `jsonschema` library:

```sh
wget https://handbook.golem.network/requestor-tutorials/vm-runtime/computation-payload-manifest.schema.json
pip install jsonschema
jsonschema --instance manifest.json computation-payload-manifest.schema.json
```

### Payload object

_Computation Payload Manifest_ **must** contain at least one _Payload_ object. 

_Payload_ definition allows to define [GVMI images](convert-a-docker-image-into-a-golem-image.md) used by Application and supported architecture.

Simple _Computation Payload Manifest_ with _Payload_ definition:

```json
{
  "version": "0.1.0",
  "createdAt": "2022-09-15T00:00:00.000000Z",
  "expiresAt": "2100-01-01T00:00:00.000000Z",
  "payload": [
    {
      "platform": {
        "arch": "x86_64",
        "os": "linux"
      },
      "urls": [
        "http://girepo.dev.golem.network:8000/docker-golem-hello-world-latest-779758b432.gvmi"
      ],
      "hash": "sha3:d646d7b93083d817846c2ae5c62c72ca0507782385a2e29291a3d376"
    }
  ]
}
```

### Computation Manifest object

_Computation Payload Manifest_ **can** contain _Computation Manifests_ object. 

With Computation Manifest object, [Requestor](../../introduction/requestor.md) constrain themselv to a certain set of allowed actions, to be negotiated with and approved by a [Provider](../../introduction/provider.md). 

Requestors' actions will be verified against the _Manifest_ during computation.

Supported _Computation Manifest_ constrains:

  - `compManifest.script`

    Defines a set of allowed ExeScript commands and applies constraints to their arguments.

    - `compManifest.script.commands` : List[Script]
  
      Specifies a curated list of commands in a form of:

      - UTF-8 encoded JSON strings

        Command context (e.g. env) or argument matching mode need to be specified for a command.

        Example: 
        
        ```json
        [
          "{
            \"run\": { 
              \"args\": \"/bin/date -R\", 
              \"env\": { 
                \"MYVAR\": \"42\", 
                \"match\": \"strict\" 
              }
            }
          }"
        ]

      - UTF-8 encoded strings

        No command context or matching mode need to be specified.

        Example: 
        
        ```json
        [
          "run /bin/cat /etc/motd", 
          "run /bin/date -R"
        ]
        ```

      - Mix of both

      Commands `deploy`, `start` and `terminate` are always allowed. These values become the default if no `compManifest.script.commands` property has been set, but the `compManifest` object is present.

    - `compManifest.script.match` : String
    
      Selects a default way of comparing command arguments stated in the manifest and the ones received in the ExeScript, unless stated otherwise in a command JSON object.

      The match property could be one of:

        - `strict`: byte-to-byte argument equality (default)

        - `regex`: treat arguments as regular expressions

          Syntax: Perl-compatible regular expressions (UTF-8 Unicode mode), w/o the support for look around and backreferences (among others).
  
  - `compManifest.net` : Object

    Applies constraints to networking.

    - `compManifest.net.inet.out` : Object

      Outgoing requests to the public Internet network constraints.

      - `compManifest.net.inet.out.protocols` : List[String]

        List of allowed outbound protocols. Currently fixed at ["http", "https"].

      - `compManifest.net.inet.out.urls : List[String]

        List of allowed external URLs that outbound requests can be sent to. E.g. ["https://api.some-public-service.com", "https://some-other-service.com/api/resource"]

Example of _Computation Payload Manifest_ with _Computation Manifest_ definition:

```json
{
  "version": "0.1.0",
  "createdAt": "2022-09-15T00:00:00.000000Z",
  "expiresAt": "2100-01-01T00:00:00.000000Z",
  "payload": [
    {
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
        "run curl.*",
        "transfer .*/output.txt"
      ],
      "match": "regex"
    },
    "net": {
      "inet": {
        "out": {
          "protocols": ["https"],
          "urls": ["https://api.some-public-service.com"]
        }
      }
    }
  }
}
```

### Certificate and Signature

A basic example of generating certificates, importing CA certificate into Provider's keystore, signing request, and sending it.

#### CA certificate

Create a basic `openssl-ca.conf` for CA certificate

```conf
[ req ]
distinguished_name  = req_dn
x509_extensions     = v3_ext

[ req_dn ]
organizationName  = Organization Name (company name)
commonName        = Common Name (your name, or app name)
emailAddress      = Email Address (support email address)

[ v3_ext ]
basicConstraints = CA:true

[ ca ]
default_ca      = CA_default

[ CA_default ]
database  = index.txt
serial    = serial.txt
policy    = policy_default

[ policy_default ]
organizationName  = match
commonName        = supplied
emailAddress      = supplied
```

Then prepare files referenced in conf

```sh
touch index.txt index.txt.attr
echo '1000' > serial.txt
```

Then generate CA certificate and key pair:

`openssl req -new -newkey rsa:2048 -days 360 -nodes -x509 -sha256 -keyout ca.key.pem -out ca.crt.pem -config openssl-ca.conf`

#### Requestor certificate signed by CA

Create a basic `openssl.conf` for Requestor's certificate.

```conf
[ req ]
distinguished_name  = req_dn
x509_extensions     = v3_ext

[ req_dn ]
organizationName  = Organization Name (company name)
commonName        = Common Name (your name, or app name)
emailAddress      = Email Address (support email address)

[ v3_ext ]
basicConstraints = CA:true
```

Then generate Requestor's Certificate Signing Request (use same `organizationName`):

`openssl req -new -newkey rsa:2048 -days 360 -sha256 -keyout requestor.key.pem -out requestor.csr.pem -config openssl.conf`

Finally sign Requestor's certificate using generated CSR and CA certificate:

`openssl x509 -req -in requestor.csr.pem -CA ca.crt.pem -CAkey ca.key.pem -CAcreateserial -out requestor.crt.pem`
