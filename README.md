# k3d.provisioner.infra
This repository provides K3D config file. 
Mainly it is designed to be managed by administrators, DevOps engineers, SREs.

## Contents
* [Requirements](#requirements)
* [Git flow strategy](#git-flow-strategy)
* [Additional information](#additional-information)
* [Development](#development)

## Requirements:
K3D = version is specified in the project file of each tenant of the repository in section `tools`.

## Git flow strategy
This repository uses the [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) approach. 
#### Stable branches: develop, master
Each merge in the master branch adds a new SemVer2 tag and a GitHub release is created.

## Additional information
* This configuration of K3D manifest can only be launched from the tenant repository via the RMK,
because the entire input set of variables is formed by the RMK at the moment 
the commands are launched: `rmk cluster k3d`.
RMK also keeps track of which version of the release of K3D config file the tenant repository will use.
The version of config file artifact is described in the project file of each 
tenant repository in the section `inventory.clusters`.

## Development
For development, you need to use one of the tenant repositories and change the code 
in the directory `.PROJECT/clusters/k3d.provisioner.infra-<version>/k3d.yaml`.
After developing and refactoring code, copy change files to this repository in feature branch and create Pull Request.
