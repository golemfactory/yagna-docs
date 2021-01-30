---
description: 'Version: 0.1 (Draft)'
---

# Compatibility Policy

## Intro

For summary of default compatibility guidelines refer [here](https://app.gitbook.com/@golem-network/s/golem-sdk-develop/see-also/compatibility-guidelines).

The purpose of the compatibility policy is to make promises to the users of Yagna software regarding the compatibility of Yagna packages against their software \(a proprietary app referencing a ya\*api library may or may not be compatible with subsequent versions of the library\) and against each other \(Requestor nodes running one version of Yagna may or may not be compatible with Provider nodes running a different version\).

**Note:** the policy must address following concerns:

* The Developer of the Requestor agent application is concerned about whether new ya\*api editions will still support his application
* The operator of a Provider node is concerned about which packages he needs to install in order to target as broad a population of Requestors as possible

**IMPORTANT:**

For the purposes of this policy we make no distinction between the App Developer and the Requestor. This is in order to simplify the compatibility guidelines, by abstracting from the compatibility dependencies between Agent Application and the components on the Requestor and Provider nodes.

## Yagna packages

A Yagna release includes Requestor and Provider packages. Each package contains a set of binaries required to setup a Requestor or Provider node, respectively.

This policy assumes a number of simplifications, without sacrificing generality:

* By **Requestor version** we consider a bundle of specific versions of following components intended to be running on Requestor node:
  * yagna daemon
  * ya\*api libraries

This implies we are not considering the compatibility between specific versions of ya\*api libraries and different versions of yagna daemon modules.

* By **Provider version** we consider a bundle of specific versions of following components meant to be running on Provider node:
  * yagna daemon
  * ya-provider agent application
  * ExeUnit and runtime modules

 This implies we are not considering the compatibility between specific versions of ya-provider application and different versions of yagna daemon and exeunit runtimes.

### Versioning scheme

Yagna packages are versioned according to the Semantic Versioning 2.0 \([https://semver.org/](https://semver.org/)\) - the most significant aspects of it are repeated below for convenience.

The version numbers are assigned using following scheme:

major.minor.patch

Where:

* major, minor, patch are incrementing integers

Following rules apply:

* For initial development \(major version = 0\) the compatibility may be broken at anytime. The APIs should not be considered stable.
* For versions 1.0+ the rules are:
* Major updates imply potentially incompatible changes to existing APIs, components and packages, eg. removal of features, APIs or modules.
* Minor updates are related to adding features to existing APIs, preserving backwards compatibility.
* Patch updates are reserved for bug fixes, maintaining compatibility.

### Compatibility concepts

We consider following compatibility relationships:

* **Requestor Agent App &lt;-&gt; Requestor package version**

By “Agent App is compatible with a specific Requestor package version” we state that Agent App is compatible with a relevant ya\*api library version associated with that Requestor version. In other words, having a yagna package 0.6.0, including yapapi version 0.4.1 we say Agent App is compatible with yagna 0.6.0 when this Agent App is dependent on yapapi 0.4.1 and is run against yagna 0.6.0 on Requestor node.

* **Requestor version &lt;-&gt; Provider version**

By “Requestor version A is compatible with Provider version B” we state that:

* a Requestor node running version A can interact over the Golem Network with a Provider node running version B in the context of Market, Activity and Payment API interaction
* A relevant ya\*api library behaviour of version A corresponds with the behaviour of ya-provider Agent and ExeUnits/runtimes of version B.

### Backward compatibility

Wherever possible, the APIs will be maintained in a backwards compatible manner. If it is necessary to change an API in a way that is not backwards compatible, a new API shall be created, and the old API will be maintained in accordance with the deprecation policy.

The behaviour of an API may change in case of bug or vulnerability fixes.

### Compatibility matrix

A matrix indicating the compatibility between Requestor and Provider versions shall be maintained \(indicative example below\):

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">Provider versions</th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Requestor versions</td>
      <td style="text-align:left"><b>0.5.0</b>
      </td>
      <td style="text-align:left"><b>0.6.0</b>
      </td>
      <td style="text-align:left"><em><b>0.7.0</b></em>
      </td>
      <td style="text-align:left">
        <p><b>MVP release</b>
        </p>
        <p>(1.0.0)</p>
      </td>
      <td style="text-align:left">
        <p><b>Minor release</b>
        </p>
        <p>(tent. 1.1.0)</p>
      </td>
      <td style="text-align:left">
        <p><b>Next major release</b>
        </p>
        <p>(tent. 2.0.0)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>0.5.0</b>
      </td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>0.6.0</b>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>0.7.0</b></em>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>MVP release</b>
        </p>
        <p>(1.0.0)</p>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">N</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Minor release</b>
        </p>
        <p>(tent. 1.1.0)</p>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">Y</td>
      <td style="text-align:left">Y</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Next major release</b>
        </p>
        <p>(tent. 2.0.0)</p>
      </td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">N</td>
      <td style="text-align:left">Y</td>
    </tr>
  </tbody>
</table>

**Notes:**

* While in Alpha mode, Yagna packages are likely to break backwards compatibility from release to release
* Once in Prod mode, major updates of Yagna Provider packages should maintain backwards compatibility up to 2 minor releases of Requestor packages
* The Provider packages are not consciously forward compatible \(ie. Provider will fall out of interest when running outdated versions\)

**IMPORTANT:**

The rules above imply a generic guideline for the Providers: by default **upgrade to the latest Provider package version available**, as that version will still support non-latest Requestors, and therefore provide widest market coverage.

### Deprecation policy

The behavior of an API or a package must not change between any two consecutive releases unless it is going through the deprecation process as described below:

* An API or component cannot be removed without notice between any two consecutive releases
* When a breaking change is required, the following process will be observed:
  * **Major release N**:
    * New methods, parameters or components to support the new functionality can be added as long as the old functionality continues to work
    * Old API is **marked as deprecated** \(in a way relevant to the language-specific deprecation labelling patterns\) and still functions properly without breaking
    * **Release notes** must include information about incoming breaking changes
  * **Major release N+1**:
    * Remove deprecated items
    * Make breaking changes
    * Announce breaking changes and end of deprecation period in **release notes**

#### Experimental features

Some features, components or API elements may be explicitly marked as experimental. The purpose of experimental features is to publish new concepts, gather community feedback and allow to stabilize.

 Experimental features may change with any release, and the change may include:

* Change of behaviour or API specification
* Removal of feature, component or API
* Promotion to stable status - from that point the default deprecation policy applies.

#### Release note sample

SUMMARY:

With this release, we are excited to share zkSync L2 Payment Driver support.

\(...\)

CHANGELOG:

* GolemSP:
  * Support golemsp stop \([\#787](https://github.com/golemfactory/yagna/pull/787)\)
* Provider:
  * Reduce timeout for closing agreements when no activity is made from 30 minutes to 90 seconds \([\#835](https://github.com/golemfactory/yagna/pull/835)\)
  * Update provider agent readme \([\#750](https://github.com/golemfactory/yagna/pull/750)\)
* \(...\)

DEPRECATED APIs:

* \[Payment API\] GetAccounts method has been marked as deprecated
* \[yapapi\] Runner class has been marked as deprecated and superseded by Executor class.
* \[...\]

API LIBRARY COMPATIBILITY:

| **Library** | **Requestor** | **Provider** |
| :--- | :--- | :--- |
| yapapi | 0.5.0+ | 0.6.0+ |
| yajsapi | 0.5.0+ | 0.6.0+ |
| ... | ... | ... |

By installing & running this software you declare that you have read understood and hereby accept the disclaimer and privacy warning found at [https://handbook.golem.network/see-also/terms](https://handbook.golem.network/see-also/terms)

## ya\*api libraries

### Versioning scheme

ya\*api libraries are versioned according to the following scheme:

major.minor.patch

Where:

* major, minor, micro are incrementing integers
* Semantic versioning 2.0 \([https://semver.org/](https://semver.org/)\) rules apply.
* ya\*api libraries are labeled with required versions of interfacing packages, eg:

   Required dependencies:

      Yagna \(Requestor\): 0.18.0+

      Yagna \(Provider\): 0.17.0+

* Within a major version we guarantee the APIs to be backward compatible, but not forward compatible. Ie. newer releases may add elements to the API, but they should not alter or remove.

