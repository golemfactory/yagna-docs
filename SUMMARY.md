# Table of contents

* [The Golem SDK documentation](README.md)

## Introduction

* [Golem overview](introduction/golem-overview.md)
* [Provider](introduction/provider.md)
* [Requestor](introduction/requestor.md)

***

* [Requestor FAQ](requestor-faq.md)
* [Provider FAQ](provider-faq.md)

## Payments

* [Payments in Golem explained](payments/payments-explained.md)
* [Layer 2 payments](payments/layer-2-payments.md)
* [Using Golem on Mainnet](payments/using-golem-on-mainnet/README.md)
  * [Your Golem wallet](payments/using-golem-on-mainnet/your-golem-wallet.md)
  * [Backing up your Golem wallet](payments/using-golem-on-mainnet/backing-up-your-golem-wallet.md)
  * [Restoring a backed-up wallet](payments/using-golem-on-mainnet/restoring-your-backed-up-golem-wallet.md)
  * [Running a requestor on Mainnet](payments/using-golem-on-mainnet/running-a-requestor-on-mainnet.md)
* [Mainnet / Polygon GLM Conversion](payments/glm-mainnet-polygon-conversion.md)

## Provider tutorials

* [Becoming a provider](provider-tutorials/provider-tutorial.md)
* [Provider CLI reference](provider-tutorials/provider-cli.md)

## Troubleshooting

* [Provider Troubleshooting](troubleshooting/provider-troubleshooting.md)
* [Requestor Troubleshooting](troubleshooting/common-issues.md)

## Developer tutorials <a href="#requestor-tutorials" id="requestor-tutorials"></a>

* [Requestor development: a quick primer](requestor-tutorials/flash-tutorial-of-requestor-development/README.md)
  * [Run first task on Golem](requestor-tutorials/flash-tutorial-of-requestor-development/run-first-task-on-golem.md)
* [Golem application fundamentals](requestor-tutorials/golem-application-fundamentals/README.md)
  * [Work generator pattern and WorkContext](requestor-tutorials/golem-application-fundamentals/hl-api-work-generator-pattern.md)
  * [Golem VPN networking concept](requestor-tutorials/golem-application-fundamentals/golem-vpn-networking-concept.md)
* [Task Model development](requestor-tutorials/task-processing-development/README.md)
  * [Introduction to the task model](requestor-tutorials/task-processing-development/task-model-introduction.md)
  * [Task Example 0: Hello World!](requestor-tutorials/task-processing-development/task-example-0-hello.md)
  * [Task Example 1: Simple hash cracker](requestor-tutorials/task-processing-development/task-example-1-cracker.md)
  * [Task Example 2: Hashcat on Golem](requestor-tutorials/task-processing-development/task-example-2-hashcat.md)
* [Service Model development](requestor-tutorials/service-development/README.md)
  * [Introduction to the service model](requestor-tutorials/service-development/service-model-introduction.md)
  * [Service Example 0: Hello world?](requestor-tutorials/service-development/service-example-0-hello-world.md)
  * [Service Example 1: Simple service](requestor-tutorials/service-development/service-example-1-simple-service.md)
  * [Service Example 2: VPN - SSH terminal](requestor-tutorials/service-development/service-example-2-vpn-ssh-terminal.md)
  * [Service Example 3: VPN - Minimalistic HTTP proxy](requestor-tutorials/service-development/service-example-3-vpn-simple-http-proxy.md)
  * [Service Example 4: Custom usage counters](requestor-tutorials/service-development/service-example-4-custom-usage-counters.md)
  * [Service Example 5: Web application](requestor-tutorials/service-development/service-example-webapp.md)
  * [Service Example 6: External API request](requestor-tutorials/service-development/service-example-6-external-api-request.md)
* [VM runtime](requestor-tutorials/vm-runtime/README.md)
  * [Creating a Docker image](requestor-tutorials/vm-runtime/creating-a-docker-image.md)
  * [Converting an image from Docker to Golem](requestor-tutorials/vm-runtime/convert-a-docker-image-into-a-golem-image.md)
  * [Testing a Golem image](requestor-tutorials/vm-runtime/gvmi-debugging.md)
  * [Uploading a Golem image](requestor-tutorials/vm-runtime/uploading-a-golem-image.md)
  * [Self-hosted VM images](requestor-tutorials/vm-runtime/self-hosted-vm-images.md)
  * [Computation Payload Manifest](requestor-tutorials/vm-runtime/computation-payload-manifest.md)
  * [Frequently asked questions](requestor-tutorials/vm-runtime/frequently-asked-questions.md)
* [Debugging with the use of log files](requestor-tutorials/debugging.md)
* [Interactive testing environment](requestor-tutorials/interactive-testing-environment/README.md)
  * [Running Goth](requestor-tutorials/interactive-testing-environment/running-goth.md)
  * [Using Test Harness to test Golem apps](requestor-tutorials/interactive-testing-environment/running-goths-interactive-mode.md)

## yapapi - Python high-level API <a href="#yapapi" id="yapapi"></a>

* [Golem Python API Reference](https://yapapi.readthedocs.io/en/latest/api.html)

## yajsapi - JavaScript API <a href="#yajsapi" id="yajsapi"></a>

* [Introduction to Golem's Java Script API](yajsapi/introduction.md)
* [High-level API development](yajsapi/high-level.md)
  * [Introduction to the task model](yajsapi/high-level/introduction.md)
    * [Task model](yajsapi/high-level/task-model.md)
    * [Hashcat](yajsapi/high-level/examples/hashcat.md)
  * [Task Example 0: Hello World!](requestor-tutorials/task-processing-development/task-example-0-hello.md)
  * [Task Example 1: Simple hash cracker](requestor-tutorials/task-processing-development/task-example-1-cracker.md)
  * [Task Example 2: Hashcat on Golem](requestor-tutorials/task-processing-development/task-example-2-hashcat.md)

* [Mid-level API development](yajsapi/mid-level.md)
  * [Introduction to the mid-level modules](yajsapi/mid-level-introduction.md)
  * TODO
  
* [Golem Java Script API Reference](yajsapi/docs/README.md)

* [Components](yajsapi/modules/README.md)
  * TODO - from typedoc

## Yagna Contributor Guide

* [How to a write payment driver](yagna-contributor-guide/payment-driver-getting-started.md)

## See also

* [Port forwarding](see-also/port-forwarding.md)
* [Running the yagna daemon from sources](see-also/running-yagna-from-sources.md)
* [Terms](see-also/terms.md)
* [Compatibility Guidelines](see-also/compatibility-guidelines.md)
* [Compatibility Policy](see-also/compatibility-policy.md)
* [Release Notes](see-also/release-notes.md)
* [Contact](see-also/contact.md)
