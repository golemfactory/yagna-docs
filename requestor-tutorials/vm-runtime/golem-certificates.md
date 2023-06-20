# Golem-certificates

## Installing cli tool

Prerequisites:

- [Rust toolchain](https://rustup.rs/)
- Git

```bash
git clone https://github.com/golemfactory/golem-certificate
cargo install --path golem-certificate/cli
```

After that, in other terminal enter UI tool by typing:

```bash
golem-certificate-cli ui
```

## Generating key-pair

Create new key-pair in `Create key pair` option in main menu and name files appropriately.

## Generating root certificate

Prerequisites:

- key-pair for your root certificate

Navigate to `Create certificate` option.
After that, put your propertiies as needed (Key usage, Validity period, Permissions and subject information) and enter your generated **public** key.
If your generated root certificate will be used to sign other certificates, be sure that you set `Key usage` to `All` or at least `Sign certificate` (or `Sign node` if you will use this certificate for signing node-descriptors).
In general, it is advised that root certificates should have `Permissions` and `Key usage` set to `All`.

Now you are able to sign your certificate.
Enter your **private** key to "Signing key" field and set "Signing certificate" as `Self-signed`.

## Generating intermediate certificate

Prerequisites:

- key-pair for your certificate certificate
- root certificate entity which will sign your certificate template

Navigate to `Create certificate` option.
After that, put your propertiies as needed (Key usage, Validity period, Permissions and subject information) and enter your generated **public** key.

Then you should save your certificate as template, and send it to root certificate entity which will sign it for you.

## Signing certificate

Prerequisites:

- key-pair for your certificate which will sign other certificate
- your certificate with appropriate `Key usage` allowing it to sign certificates (`Sign certificate` field or `All`)
- template of certificate which you want to sign

Firstly, check if certificate template which you got does not request more `Permissions`, `Key usage` or `Validity Period` than your certificate has.
If template requests more, error will be returned in signing process.
Navigate to `Create certificate` option and load from desired template.
Enter your **private** key to "Signing key" field and then `Load signing certificate` from file in the "Signing certificate" field.

## Generating node-descriptor

Prerequisites:

- your node-id

Navigate to `Create node descriptor` option.
After that, put your properties as needed (your node-id, appropriate permissions and validity period).

Then you should save your certificate as template, and send it to certificate entity which will sign it for you.

## Signing node-descriptor

Prerequisites:

- key-pair for your certificate which will sign node-descriptor
- your certificate with appropriate `Key usage` allowing it to sign nodes (`Sign node` field or `All`)
- node-descriptor template

Firstly, check if node-descriptor template which you got does not request more `Permissions` or `Validity Period` than your certificate has.
If template requests more, error will be returned in signing process.
Navigate to `Create node descriptor` option and load from desired template.
Enter your **private** key to "Signing key" field and then `Load signing certificate` from file in the "Signing certificate" field.
