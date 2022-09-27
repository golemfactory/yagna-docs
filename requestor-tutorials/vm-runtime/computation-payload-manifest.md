---
description: Computation Payload Manifest description, its schema, and configuration guide
---

# Computation Payload Manifest

_Computation Payload Manifest_ allows [Requestor](../../introduction/requestor.md) to define application package _Payload_ and allows to set constraints on _Computations_ performed on [Provider](../../introduction/provider.md) node.

Request with a manifest can be [configured in yapapi](#configuration). 

Provider node operator controls what computation can be performed by:

  - [Importing certificates](#3-importing-application-authors-certificates) used to sign App authors' certificates into Provider's [keystore](../../provider-tutorials/provider-cli.md#keystore) (which allows to verify _manifest_ signature)

  - Adding domain patterns to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist) (which makes [signature](#2-manifest-signature) optional _manifests_)

## Configuration

Manifest can be configured as a [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function parameter together with optional manifest signature and [App author's certificate](#certificates).

Check [external API request example](../service-development/service-example-6-external-api-request.md) for details.

## Manifest schema

<!-- 
Schema generated using: https://github.com/golemfactory/yagna/blob/2088-computation-payload-manifest-schema/utils/manifest-utils/README.md#computation-payload-manifest-schema
Schema doc generated using: https://github.com/CesiumGS/wetzel 
cmd: wetzel computation-payload-manifest.schema.json -w -p computation-payload-manifest.schema.json -s computation-payload-manifest.schema.md > computation-payload-manifest.schema.md
 -->
_Computation Payload Manifest_ must follow a specific [JSON Schema](computation-payload-manifest.schema.json) ([Documentation](computation-payload-manifest.schema.md))

### Schema verification

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

  - #### `compManifest.script`

    Defines a set of allowed ExeScript commands and applies constraints to their arguments.

    - #### `compManifest.script.commands` : List[Script]
  
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

    - #### `compManifest.script.match` : String
    
      Selects a default way of comparing command arguments stated in the manifest and the ones received in the ExeScript, unless stated otherwise in a command JSON object.

      The match property could be one of:

        - `strict`: byte-to-byte argument equality (default)

        - `regex`: treat arguments as regular expressions

          Syntax: Perl-compatible regular expressions (UTF-8 Unicode mode), w/o the support for look around and backreferences (among others).
  
  - #### `compManifest.net` : Object

    Applies constraints to networking.

    - #### `compManifest.net.inet.out` : Object

      Outgoing requests to the public Internet network constraints.

      - #### `compManifest.net.inet.out.protocols` : List[String]

        List of allowed outbound protocols. Currently fixed at ["http", "https"].

      - #### `compManifest.net.inet.out.urls` : List[String]

        List of allowed external URLs that outbound requests can be sent to. E.g. ["https://api.some-public-service.com", "https://some-other-service.com/api/resource"]

#### Example of _Computation Payload Manifest_ with _Computation Manifest_ definition:

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

### Certificates

_App author's certificate_ gets send in a request together with a _Computation Payload Manifest_ and its signature. Certificate is used to verify signature. In order to verify signature _Provider_ first needs to verify incoming _App author's certificate_. To do so it has to have certificate used to sign _App author's certificate_ [imported](#3-importing-application-authors-certificates) into its keystore (together with every intermediate certificate in the chain).

#### Manifest signature

Signature allows _Provider_ to verify content of incoming _Computation Payload Manifest_.

It can be generated using `openssl` tool and a private key related to _App author's certificate_ signed by some trusted by _Providers_ certificate.

Signature needs to be generated from content of the _Computation Payload Manifest_ encoded in `base64`:

```sh
openssl dgst -sha256 -sign author.key -out manifest.json.base64.sign.sha256 manifest.json.base64
# both Signature and App Author Certificate need to be sent in base64 encoded form
base64 manifest.json.base64.sign.sha256 --wrap=0 > manifest.json.base64.sign.sha256.base64
base64 author.crt.pem --wrap=0 > author.crt.pem.base64
```

#### Self signed certificate example

A basic example of generating self signed root CA certificate to sign App author's certificate, and then importing generated root CA certificate into Provider's keystore.

##### 1. Generating self signed root CA certificate

Create `openssl-ca.conf` for CA certificateL

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

Then prepare referenced in config files:

```sh
touch index.txt index.txt.attr
echo '1000' > serial.txt
```

Then generate CA certificate and key pair:

`openssl req -new -newkey rsa:2048 -days 360 -nodes -x509 -sha256 -keyout ca.key.pem -out ca.crt.pem -config openssl-ca.conf`

##### 2. Generating Requestor certificate

Create `openssl.conf` for App author's certificate:

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

Then generate _App author's certificate_ Signing Request (use same `organizationName`):

`openssl req -new -newkey rsa:2048 -days 360 -sha256 -keyout author.key.pem -out author.csr.pem -config openssl.conf`

Finally generate _App author's certificate_ using CSR and CA certificate:

`openssl x509 -req -in author.csr.pem -CA ca.crt.pem -CAkey ca.key.pem -CAcreateserial -out author.crt.pem`

##### 3. Importing application author's certificates

To import certificate into the keystore use [`ya-provider keystore add`](../../provider-tutorials/provider-cli.md#keystore) command:

`ya-provider keystore add ca.crt.pem`
