---
description: Computation Payload Manifest description and schema
---

# Computation Payload Manifest

_Computation Payload Manifest_ allows [Requestor](../../introduction/requestor.md) to define application package _Payload_ and to set constraints on _Computations_ performed on [Provider](../../introduction/requestor.md) node.

## Schema

<!-- 
Schema generated using: https://github.com/golemfactory/yagna/blob/2088-computation-payload-manifest-schema/utils/manifest-utils/README.md#computation-payload-manifest-schema
Schema doc generated using: https://github.com/CesiumGS/wetzel 
cmd: wetzel computation-payload-manifest.schema.json -w -p computation-payload-manifest.schema.json -s computation-payload-manifest.schema.md > computation-payload-manifest.schema.md
 -->
_Computation Payload Manifest_ must follow a specific [JSON Schema](computation-payload-manifest.schema.json) ([Documentation](computation-payload-manifest.schema.md))

Manifest can be verified using `jsonschema` library:

```sh
pip install jsonschema
wget https://handbook.golem.network/requestor-tutorials/vm-runtime/computation-payload-manifest.schema.json
jsonschema --instance manifest.json computation-payload-manifest.schema.json
```

### Payload

_Computation Payload Manifest_ **must** contain at least one _Payload_ definition. 

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

### Computation Manifest

_Computation Payload Manifest_ **can** contain _Computation Manifests__ definition. 

With Computation Manifests, [Requestors](../../introduction/requestor.md) constrain themselves to a certain set of allowed actions, to be negotiated with and approved by a [Provider](../../introduction/requestor.md). 

Requestors' actions will be verified against the Manifest during computation.

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
          "urls": ["https://api.public.com"]
        }
      }
    }
  }
}
```

## Configuration

Manifest can be configured in a service payload using [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function together with sometimes required [signature and app author's certificate](#signature).

Provider node operator controls what work can be performed by:

* Importing public certificates of trusted application authors to Provider's [keystore](../../provider-tutorials/provider-cli.md#keystore)

* Adding domain patterns to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist)

### Signature

