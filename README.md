# k3d.provisioner.infra

This repository provides [K3D](https://k3d.io) config file. 
Mainly it is designed to be managed by administrators, DevOps engineers, SREs.

## Contents

* [Requirements](#requirements)
* [Git workflow](#git-workflow)
* [Additional information](#additional-information)
* [Development](#development)

## Requirements

`K3D` = version is specified in the [project.yaml](https://github.com/edenlabllc/rmk/blob/develop/docs/configuration/project-management/preparation-of-project-repository.md#projectyaml) file 
of each project of the repository in the `tools` section.

## Git workflow

This repository uses the classic [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) workflow, 
embracing all its advantages and disadvantages.

**Stable branches:** develop, master

Each merge in the master branch adds a new [SemVer2](https://semver.org/) tag and a GitHub release is created.

## Additional information

This configuration of K3D manifest can only be launched from the project repository via [RMK](https://github.com/edenlabllc/rmk),
because the entire input set of variables is formed by the RMK at the moment 
the commands are launched: `rmk cluster k3d`.
RMK also keeps track of which version of the release of K3D config file the project repository will use.
The version of config file artifact is described in the project file of each 
project repository in the section:

```yaml
inventory:
  clusters:
    k3d.provisioner.infra:
      version: <SemVer2>
      url: git::https://github.com/edenlabllc/{{.Name}}.git?ref={{.Version}}
```

## Development

For development, you need to use one of the project's repositories and change the code 
in the directory `.PROJECT/clusters/k3d.provisioner.infra-<version>/k3d.yaml`.
After developing and refactoring code, copy change files to this repository in feature branch and create Pull Request.
