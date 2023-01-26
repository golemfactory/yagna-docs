---
description: Golem daemon extensions
---

# Overview

Autostart extensions are executed during startup of the daemon process. The "autostart" option can be configured
via `yagna`'s CLI or by placing an [extension manifest](#manifest) next to the extension binary.

Please refer to the [designated directory list](README.md#designated-directories) to find out where to install an extension.

## Autostart CLI

Assuming that there is a `yagna-xchange` extension installed, we can execute that extension on daemon startup by typing the following:

```bash
yagna extension register xchange usd
```

The command above will create a manifest file next to the binary, informing the daemon that `yagna-xchange` should be executed on startup with appropriate arguments.

`yagna extension list` should now report an output similar to:

```bash
┌────────────┬─────────────┬─────────────────────────────────────────────┬────────┐
│    name    │  autostart  │  path                                       │  args  │
├────────────┼─────────────┼─────────────────────────────────────────────┼────────┤
│   xchange  │      x      │  /home/user/.local/bin/yagna-xchange        │  usd   │
└────────────┴─────────────┴─────────────────────────────────────────────┴────────┘
```

In order to disable autostart, run

```bash
yagna extension unregister <name>
```

`yagna extension list` should now report an output similar to:

```bash
┌────────────┬─────────────┬─────────────────────────────────────────────┬────────┐
│    name    │  autostart  │  path                                       │  args  │
├────────────┼─────────────┼─────────────────────────────────────────────┼────────┤
│   xchange  │             │  /home/user/.local/bin/yagna-xchange        │  usd   │
└────────────┴─────────────┴─────────────────────────────────────────────┴────────┘
```

Since each call to `extension list` performs an extension binary lookup, we can tell that the process involves
parsing each extension's manifest file to display appropriate information.

## Manifest

Manifest files describe whether and how extensions should be executed on daemon startup. Their inclusion in the 
extension package is optional.

A manifest file must be placed next to the extension binary. The name is composed of the binary file stem and a JSON
extension (e.g. `yagna-xchange.json`).

### Format

```json
{
  "args": [],
  "env": {},
  "autostart": true
}
```

- `args`

  Command line arguments passed to the extension binary.

- `env`

  A dictionary of environment variables and their string values passed to the extension binary. 

- `autostart`

  A boolean value determining whether the extension should be started together with the `yagna` daemon.

# Creating your own extension

Developers are required to build their extension as a standalone binary; the programming language can be of their choosing.

## Execution lifecycle

Each autostart extension binary is:

1. Executed in a last stage of daemon's startup process.

  - the API is ready to serve requests
  - all CLI commands are ready to be executed

2. Restarted on failure.

  If the extension process terminates with a code other than 0, the extension is restarted with a fixed, 3-second delay.
    
4. Terminated together with the daemon.

  Developers may choose to keep the extension process running when the daemon terminates. 
  This can be achieved by detaching the process from the parent process group / forking into background.

If an extension binary fails on any stage of execution, `yagna` daemon execution will not be interrupted.
Users can expect to see an appropriate warning message in the log.

## Environment variables

`yagna` executes autostart extensions with the following environment variables set:

- `YAGNA_DATA_DIR`

  The path to `yagna`'s data directory. 

- `YAGNA_API_URL`

  Rest API HTTP address to connect to.

- `YAGNA_NODE_ID`

  The default Node ID used by `yagna` daemon.

- `YAGNA_APP_KEY` (optional)

  An API key corresponding to the default Node ID. May not be present if not configured beforehand by the user.


## Standard input and output

All information printed out by the binary is prefixed with extension's name and written to daemon's log. Keyboard input
cannot be read in "autostart" mode.
