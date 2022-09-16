---
description: Computation Payload Manifest description and schema
---

# Computation Payload Manifest

_Computation Payload Manifest_ allows [Requestor](../../introduction/requestor.md) to define application package _Payload_ and allows to set constraints on _Computations_ performed on [Provider](../../introduction/requestor.md) node.

It can be [configured](#configuration) as a parameter of [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function. 


## Schema

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

With Computation Manifests, [Requestors](../../introduction/requestor.md) constrain themselves to a certain set of allowed actions, to be negotiated with and approved by a [Provider](../../introduction/requestor.md). 

Requestors' actions will be verified against the _Manifest_ during computation.

Supported _Computation Manifest_ constrains:

  - `compManifest.script`

    Defines a set of allowed ExeScript commands and applies constraints to their arguments.

    - `compManifest.script.commands` : List[Script]
  
      Specifies a curated list of commands in form of:

      - UTF-8 encoded strings

        No command context or matching mode need to be specified.

        Example: 
        
        ```json
        [
          "run /bin/cat /etc/motd", 
          "run /bin/date -R"
        ]
        ```

      - UTF-8 encoded JSON strings

        Command context (e.g. env) or argument matching mode need to be specified for a command.

        Example: 
        
        ```json
        [
          "{\"run\": { 
              \"args\": \"/bin/date -R\", 
              \"env\": { 
                \"MYVAR\": \"42\", 
                \"match\": \"strict\" 
              }
            }
          }"
        ]
        ```

      - mix of both

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

        List of allowed external URLs that outbound requests can be sent to. E.g. ["http://golemfactory.s3.amazonaws.com/file1", "http://golemfactory.s3.amazonaws.com/file2"]


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

## Configuration

Manifest can be configured in a service payload using [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function together with sometimes required [signature and app author's certificate](#signature).

Provider node operator controls what work can be performed by:

* Importing public certificates of trusted application authors to Provider's [keystore](../../provider-tutorials/provider-cli.md#keystore)

* Adding domain patterns to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist)

### Signature

TODO