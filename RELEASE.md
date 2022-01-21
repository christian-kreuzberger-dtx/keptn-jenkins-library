# Releasing

A new version of the Keptn Jenkins library is released as needed when
there are fixes and features ready.

## Versioning

The versioning of the Keptn Jenkins library follows [semver](https://semver.org/).
This means, every version number consists of three parts (x.y.z) that have a
different meaning and describe the type of change this version introduces.

- **Patch:** (x.y.**z**): A patch version only includes fixes and small patches.
- **Minor:** (x.**y**.z): A minor version includes new features that do **NOT**
  introduce a breaking change.
- **Major:** (**x**.y.z): A major version is the only version that can contain
  breaking changes.

## How to release

### Typical case: create a new version TODO: change it to use actions
Go to the [releases
page](https://github.com/keptn-sandbox/keptn-jenkins-library/releases) of
[keptn-sandbox/keptn-jenkins-library](https://github.com/keptn-sandbox/keptn-jenkins-library/)
repository and create a new release using the appropriate tag in semver format
(creating it if it doesn't exist yet) on the appropriate branch (`master` most
of the time).  Make sure to provide a description and auto-generate release
notes using the github UI.

### Special cases: bugfixing and hotfixes for older versions

Bugs must be fixed on master first and then backported to the appropriate versions.

If the target major and minor versions onto which backport the fix are the same
as the latest version released from master the usual procedure described in the
previous paragraph is sufficient and a new release can be created simply
increasing the patch number of the latest release.

If the fixes must be ported to older library versions, a `release branch`
starting from the last commit on master that has been tagged with the same
major and minor version should be used (creating it if necessary) using the
format `<major version>.<minorversion>.x`.

Once the backport of the fix is present on the release branch a new release for
the same major/minor version can be created on such branch by increasing the
patch version as usual.

For *critical* fixes a hotfix of a specific patch version can be created using
a `hotfix branch` that starts at the **exact major, minor and patch version**
using the format `<major version>.<minor version>.<patch version>-hotfix` and
tagging the version as `x.y.z-**n**` where n is the progressive number of the
hotfixes applied (hopefully only 1 is needed). Contrary to the bugfix process,
hotfix releases should be used only in exceptional cases where it's impossible
for the user to move to a newer patch version.  The need for hotfixes will be
evaluated on a case-by-case basis depending on the impact of the issue.
