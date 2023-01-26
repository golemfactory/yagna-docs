---
description: Golem command line extensions
---

# Overview

Command line extensions augment the command line interface of `yagna` and `golemsp` with new commands.

## Extension execution process

Assuming that there is a `yagna-xchange` entry listed within `yagna extension list`,
we can now type (e.g.)`golemsp xchange usd` in our terminal to run the extension binary.

### Successful execution

1. User executes a `golemsp xchange usd` command
   
   This command is not native to `golemsp`, all arguments are forwarded to the main `yagna` binary.

2. `golemsp` executes a `yagna xchange usd` command

   Command is not a `yagna` built-in, the extension discovery process commences.

3. Extension binary lookup

   This step is executed for each unknown command. `yagna` will traverse each
   [known directory](README.md#designated-directories) to find the `yagna-xchange` file.

4. `yagna` executes a `yagna-xchange usd` command

   All information printed out by the binary is sent to the running terminal.
   The extension is allowed to prompt the user for input when necessary.

### Unknown extension

When an extension binary lookup fails (point 3. above), the user is presented with a help message corresponding to the executed binary.
I.e. `golemsp xyz` will print a message identical to `golemsp --help`, whereas executing `yagna xyz` will print usage of the `yagna` binary.

# Creating your own extension

Developers are required to build their extensions as standalone binaries; the programming language can be of their choosing.

## Environment variables

`yagna` executes command line extensions with the following environment variables set:

- `YAGNA_DATA_DIR`
  
  The path to `yagna` daemon's data directory. 

- `YAGNA_JSON_OUTPUT`

  Values of `true` or `false` determine whether JSON output is expected.
