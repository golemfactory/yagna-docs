---
description: Golem Provider command line interface
---

# Provider CLI



* `golem status` Display general status, state, latest jobs and wallet info
* `golem settings` Manage settings
  * SUBCOMMANDS:
    * `show` Show current settings
    * `set` Change settings
    * `help` Prints this message or the help of the given subcommand\(s\)
      * `golem settings show`
      * `golem settings set`
        * `golem settings set presets`
          * `golem settings set presets <default>`
          * `golem settings set presets <follow_market>` ?
          * `golem settings set presets <slow>`
          * `golem settings set presets <mid>`
          * `golem settings set presets <max>`
        * `golem settings set cores` Set number of shared CPU cores \[≥1\]
        * `golem settings set memory` Set number of shared RAM \[GB\]
        * `golem settings set disk` Set number of disk space \[GB\]
        * `golem settings set password` Set new or change password
      * `golem settigs env`
      * `golem settings cache clear`
      * `golem settings id create`
* `golem backup`
  * `golem backup key export`
  * `golem backup key import`
* `golem stop` Stop Golem
* `golem pause/resume`
* `golem help` Prints this message or the help of the given subcommand\(s\)

