---
description: Yagna extensions
---

# Extensions

## What is an extension?

The extension system is an opinionated way of enhancing the command line interface of `yagna` / `golemsp` and
executing third-party integrations side by side with the `yagna` daemon.

Each extension is a standalone binary that is automatically discovered by `yagna` / `golemsp` if:

- the binary's name is prefixed with `yagna-` 
- the binary is saved to [a location discoverable by `yagna`](#designated-directories)

Each extension can be a [command line interface argument](cli.md), a binary [started together with the yagna daemon](daemon.md) or a combination of both. 
Developers are free to choose the language their extension will be developed in.

## Extension discovery

Extension discovery is executed with each invocation of a command that is native neither to `yagna` nor `golemsp`, and
also when the `yagna` daemon process has started executing. All native commands can be listed with `yagna --help` or `golemsp --help`.

In order to manually trigger the discovery process one can type `yagna extension list` in their terminal.

```bash
┌────────────┬─────────────┬─────────────────────────────────────────────┬────────┐
│    name    │  autostart  │  path                                       │  args  │
├────────────┼─────────────┼─────────────────────────────────────────────┼────────┤
│   xchange  │             │  /home/user/.local/bin/yagna-xchange        │  usd   │
└────────────┴─────────────┴─────────────────────────────────────────────┴────────┘
```

where `/home/user/.local/bin` is a directory present in the `PATH` environment variable.

With this setup, the following commands become available:

- `yagna xchange`
- `golemsp xchange`

Both applications can now recognize the new `xchange` command and will no longer print an error (or "usage") message.

## Installing extensions

The [provider](../provider-tutorials/provider-tutorial.md) and [requestor]() installation scripts
will help you with installing extensions appreciated by the community and recognized by the Golem Factory.

Other extensions can be placed by the user in one of the designated directories.

## Designated directories

Extension binaries can be placed on the following paths: 

- one present in the `PATH` environment variable
- designated extension directory:
  - `~/.local/lib/yagna/extensions` (Linux, macOS)
  - `%APPDATA%\Roaming\GolemFactory\yagna\extensions` (Windows)
- `extensions` subdirectory in `yagna`'s binary parent directory

Additionally, each extension may be placed in its own subfolder, having its assets organized. 
E.g. an extensions' directory tree may be organized as follows:

```
~/.local/lib/yagna/extensions
├── yagna-xchange
└── yagna-dashboard
    ├── yagna-dashboard
    ├── yagna-dashboard.json
    ├── config.db
    └── www
        ├── index.html
        ├── script.js
        └── style.css
```
