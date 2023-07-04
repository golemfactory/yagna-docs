# Golem-certificates

## Installing the cli tool

Prerequisites:

- [Rust toolchain](https://rustup.rs/)
- Git

```bash
git clone https://github.com/golemfactory/golem-certificate
cargo install --path golem-certificate/cli
```

After that, in another terminal, enter the UI tool by typing:

```bash
golem-certificate-cli ui
```

## Generating a key-pair

Create a new key-pair using the `Create key pair` option in the main menu and name the files appropriately.

## Generating a root certificate

Prerequisites:

- key-pair for your root certificate

Navigate to the `Create certificate` option.
After that, put your propertiies as needed (Key usage, Validity period, Permissions and subject information) and enter your generated **public** key.
If your generated root certificate will be used to sign other certificates, be sure that you set `Key usage` to `All` or at least `Sign certificate` (or `Sign node` if you intend to use this certificate to sign node descriptors).
In general, it is advised that root certificates should have `Permissions` and `Key usage` set to `All`.

Now you are able to sign your certificate.
Enter your **private** key into the "Signing key" field and set "Signing certificate" as `Self-signed`.

## Generating an intermediate certificate

Prerequisites:

- a key-pair for your certificate
- a root certificate entity which will sign your certificate template

Navigate to the `Create certificate` option.
After that, put your propertiies as needed (Key usage, Validity period, Permissions and subject information) and enter your generated **public** key.

Then you should save your certificate as a template, and send it to the root certificate entity which will sign it for you.

## Signing a certificate

Prerequisites:

- a key-pair for your certificate which will sign another certificate
- your certificate with an appropriate `Key usage`, allowing it to sign other certificates (`Sign certificate` field or `All`)
- a template of the certificate you want to sign

Navigate to `Create certificate` option and load from desired template.
Then check if the certificate template which you got does not request more `Permissions`, `Key usage` or `Validity Period` than your own certificate has.
If the template requests more, an error will be returned in the signing process.
Enter your **private** key into the "Signing key" field and then `Load signing certificate` from a file in the "Signing certificate" field.

## Generating a node-descriptor

Prerequisites:

- your node-id

Navigate to the `Create node descriptor` option.
After that, put your properties as needed (your node-id, appropriate permissions and the validity period).

Then you should save your certificate as a template, and send it to the certificate entity which will sign it for you.

## Signing a node descriptor

Prerequisites:

- a key-pair for your certificate which will sign the node descriptor
- your certificate with appropriate `Key usage` allowing it to sign nodes (`Sign node` field or `All`)
- a node descriptor template

First, check if the node descriptor template which you got does not request more `Permissions` or `Validity Period` than your own certificate has.
If the template requests more, an error will be returned in the signing process.
Navigate to `Create node descriptor` option and load from the desired template.
Enter your **private** key into the "Signing key" field and then `Load signing certificate` from the file into the "Signing certificate" field.
