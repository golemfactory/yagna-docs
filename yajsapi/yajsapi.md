# Introduction to Golem's high-level Java Script API

yajsapi / [Exports]()

Ya**JS**api   
  


### Prerequisites

* [node](https://nodejs.org/en/) &gt;= v12.13.0
* [yarn](https://classic.yarnpkg.com/en/docs/install/) &gt;= v1.22.3

## Building the Library

_\(not needed for running examples\)_

#### Installation

* run `yarn` in main folder

#### Building

* run `yarn build` in main folder
* build is ready in `dist` folder!

## Running Examples

#### Installation

* `cd examples`         will take you to examples folder
* `yarn`                will install dependencies for the examples
* add `YAGNA_APPKEY` as environment variable; 

  ```text
  export YAGNA_APPKEY=your_yagna_app_key_here
  ```

#### When ready

* `npm run js:blender`  will start blender javascript example
* `npm run ts:blender`  will start blender typescript example
* `npm run js:low`      will start javascript low level api example
* `npm run ts:low`      will start typescript low level api example

#### Need more logs

Call `-d` or `--debug` flag on your example script, e.g. `npm run ts:blender -- -d`

#### Subnet

Use the `--subnet-tag` option, e.g. `npm run ts:blender -- --subnet-tag YOUR_SUBNET`.

