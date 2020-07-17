---
description: 'Golem network provider installation, configuration and usage'
---

# Provider tutorial

## How can I benefit from running the provider on mine hardware?

After installing and running the golem provider you will benefit in the following way:

* serving other actors in the golem network that are in need of IT resources that your hardware is not using
* payments for the resources your share

The payments are done through [ethereum](https://ethereum.org/), so the whole process is very simple!

The typical use case is as follows: after receiving input data, the processing is done by your hardware, output data being sent back to the requestor, the ethereum payment is done. It is that simple.

![Typical golem network use case](../.gitbook/assets/provider-tutorial-benefit%20%281%29.png)

## Installation prerequisites

Download the installation pack from \[TO DO: provide the installation link\].

## Installation

Open your terminal and type

```text
dpkg -i <link to downloaded pack>
```

press enter and wait for Golem to install on your machine.

## Running the provider

To run Golem type in the terminal:

```text
golem start
```

## First-time use

{% hint style="info" %}
If you are running your Golem node for the first time you will be asked to set up a few simple things. You will be able to change those settings later on in your Golem settings.
{% endhint %}

After starting golem for the first time, the following questions are displayed at the console: ****

```text
To continue using Golem please accept our Terms and conditions:
```

* `Y` - accept the terms
* `N` - decline the terms. You will not be able to use the Golem Node
* `View` - view the T&C

```text
Please paste your Ethereum address that will be used in Golem to collect 
your earnings. You will be able to change this address later on in your 
Golem settings.
```

* Paste external Ethereum address
* Confirm
  * `Y`
  * `N`

```text
Set the name of your Golem Node that will be visible to other users
```

Set the new name of your node and press ENTER \(warning about the public name\)

{% hint style="success" %}
Congratulations! Now you can start using the Golem Provider! 
{% endhint %}

{% hint style="info" %}
Your Golem Node will start with the _Default config_:

* CPU - 2 cores
* RAM - 2 GB
* Disk - 200 MB
* Market: GNT value

You can change those settings in the settings menu later on.
{% endhint %}

{% hint style="info" %}
To check the logs, type:

```text
golem logs
```
{% endhint %}

## Getting the job status

To display general status, state, latest jobs and wallet info, type the following in the new terminal window:

```text
golem status
```

## Changing the run state

### Stopping the provider

To stop the provider daemon, type:

```text
golem stop
```

### Pausing the provider

To pause the provider daemon, type:

```text
golem pause
```

### Resuming the provider

To resume the provider daemon that is in pause mode, type:

```text
golem resume
```

## Provider configuration

To get the current configuration, type the following in the new terminal window:

```text
golem settings show
```

### CPU usage limit

To change the provider's CPU usage limit, type:

```text
golem settings set --cores [number]
```

### Memory usage limit

To change the provider's memory usage limit, type:

```text
golem settings set --memory [number]
```

### Disk usage limit

To change the provider's disk usage limit, type:

```text
golem settings set --disk [number]
```



The complete configuration guide, please check following:

{% page-ref page="../provider-reference/provider-cli.md" %}



## Next steps





