# Rug Archive

[![Build Status](https://travis-ci.org/atomist-rugs/rug-archive.svg?branch=master)](https://travis-ci.org/atomist-rugs/rug-archive)
[![Slack Status](https://join.atomist.com/badge.svg)](https://join.atomist.com)

This [Rug][rug] archive contains a Generator for a Rug Archive
project.  Meta, isn't it?

[rug]: http://docs.atomist.com/

After you create a project with this generator, you may enjoy the compatible editors in [atomist-rugs:rug-editors](https://github.com/atomist-rugs/rug-editors).

## Rugs

### NewRugArchiveProject

The NewRugArchiveProject generator creates a new Rug archive project.

#### Prerequisites

There are no prerequisites to running this generator.

#### Parameters

To run this generator, you must supply the following parameters.

Name | Required | Default | Description
-----|----------|---------|------------
`project_name` | Yes | |  A valid GitHub repository name.  It must be 21 characters or less to avoid truncating name when the its Slack channel is created.
`group_id` | No | mygroup |  Maven group ID, e.g., "company-rugs".  Typically the GitHub owner of the repo being created is used.
`version` | No | 0.1.0 | [Semantic version][semver] of the project.
`description` | No | My new project | A brief description of the project.

[semver]: http://semver.org

#### Running

Run it as follows:

```
$ cd parent/directory
$ rug generate atomist-rugs:rug-archive:NewRugArchiveProject \
    ruggery \
    group_id=persian-rugs \
    version=0.1.0 \
    description="Rug Archive to hold my Rugs"
```

Note the first parameter, the `project_name`, is different in that you
do not need to supply the name of the parameter, just the value.  This
is because the `project_name` parameter is required for all
generators.  This will create a directory named `ruggery` and populate
it with a working Rug Archive project.  If you are happy with the
change, commit the changes.

```
$ cd ruggery
$ git init
$ git add .
$ git commit -m 'Initial version generated by Atomist'
```

See the README in the generated project for further instructions.

### AddBasicRugArchiveManifestYml

The AddBasicRugArchiveManifestYml editor creates the files needed in a
Rug Archive project.

#### Prerequisites

An existing project.

#### Parameters

To run this editor, you must supply the following parameters.

Name | Required | Default | Description
-----|----------|---------|------------
`project_name` | Yes | |  A valid GitHub repo name containing only alphanumeric, ., -, and _ between one and 100 characters long.
`group_id` | No | mygroup |  Maven group ID, e.g., "company-rugs".  Typically the GitHub owner of the repo being created is used.
`version` | No | 0.1.0 | [Semantic version][semver] of the project.

#### Running

Run it as follows:

```
$ cd rug/project/directory
$ rug edit atomist-rugs:rug-archive:AddBasicRugArchiveManifestYml \
    project_name=ruggery \
    group_id=persian-rugs \
    version=0.1.0
```

Since this is an editor, the `project_name` parameter is specified
using the standard `paramenter_name=parameter_value` syntax.  This
will create the `.atomist` directory and the `manifest.yml` file
within it.

## Support

General support questions should be discussed in the `#support`
channel on our community Slack team
at [atomist-community.slack.com][slack].

If you find a problem, please create an [issue][].

[issue]: https://github.com/atomist-rugs/rug-archive/issues

## Development

You can build, test, and install the project locally with
the [Rug CLI][cli].

[cli]: https://github.com/atomist/rug-cli

```
$ rug test
$ rug install
```

To create a new release of the project, simply push a tag of the form
`M.N.P` where `M`, `N`, and `P` are integers that form the next
appropriate [semantic version][semver] for release.  For example:

[semver]: http://semver.org

```
$ git tag -a 1.2.3
```

The Travis CI build (see badge at the top of this page) will
automatically create a GitHub release using the tag name for the
release and the comment provided on the annotated tag as the contents
of the release notes.  It will also automatically upload the needed
artifacts.

---
Created by [Atomist][atomist].
Need Help?  [Join our Slack team][slack].

[atomist]: https://www.atomist.com/
[slack]: https://join.atomist.com/
