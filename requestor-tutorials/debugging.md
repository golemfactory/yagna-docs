---
description: Introducing log files
---

# Debugging

When developing applications on Golem, sooner or later you will get to a point where something is not working as expected. Executing commands on the provider-hosted container seems to be one of the most error-prone areas. If something is going wrong on the provider side, we need to have a tool that helps us in problem identification. When we know what are the error details it usually is much easier to correct our code and thus eliminate the bug.

## Introducing log files

The good news is that Golem high-level API supports log files. The log files contain all sorts of interesting stuff. Among others you will find there:

* Requestor &gt; Provider file transfer details
* Output streams of executing commands on the Provider: `stdout` and `stderr`
* Provider &gt; Requestor file transfer details

## How to enable logging?

The logging infrastructure in Golem's high-level API is quite universal and thus complicated, but for most of the cases using the `SummaryLogger` will do the job. 

{% hint style="info" %}
The `SummaryLogger`is an event listener that listens to all the atomic events and combines them into the more aggregated track of events that is easier to grasp by humans.
{% endhint %}

To enable logging to a file we need two things:

```python
enable_default_logger(log_file=args.log_file)
```

`enable_default_logger` enables default logger that: 

* outputs to the Requestor application's `stderr` all the log messages with the level `INFO`
* if the `log_file` is specified, outputs to the file specified all the log messages with the level `INFO` and `DEBUG`

Then in the `Executor`we need to:

```python
    async with Executor(
        ...
        event_consumer=log_summary(log_event_repr),
        ...
    ) as executor:
```

The `log_summary` creates `SummaryLogger` instance that is passed as event consumer to the Executor we are creating.

## Let's have an error

Let's look at the yacat example code.

{% embed url="https://github.com/golemfactory/yapapi/blob/master/examples/yacat/yacat.py" %}





## Reading the log file

## Fixing the error

## Log files - what else is there?

## Docker exec - an alternative approach 



