---
description: Computation Payload Manifest description and schema
---

# Computation Payload Manifest

_Computation Payload Manifest_ allows a [Requestor](../../introduction/requestor.md) to declare the constraints for a work which may be performed on a [Provider](../../introduction/requestor.md) node.

## Schema

_Computation Payload Manifest_ must follow a specific [JSON Schema](computation-payload-manifest.schema.json)

Newly created manifest can be verified using `jsonschema` library:

```sh
pip install jsonschema
wget https://handbook.golem.network/requestor-tutorials/vm-runtime/computation-payload-manifest.schema.json
jsonschema --instance manifest.json computation-payload-manifest.schema.json
```

## Configuration

It can be configured in a service payload using [yapapi.payload.vm.manifest](https://yapapi.readthedocs.io/en/latest/api.html#module-yapapi.payload.manifest) function together with *optional* app author's [certificate]() and manifest's signature [signature]().

Provider node operator controls what work can be performed by:

* Importing public certificates of trusted application authors to Provider's [keystore](../../provider-tutorials/provider-cli.md#keystore)

* Adding domain patterns to Provider's [domain whitelist](../../provider-tutorials/provider-cli.md#domain-whitelist)
