# Vagrant tool
## Description

Vagrant works as a Virtual Machine orchestrator. Since Docker for Windows has some work issues, Vagrant helps developers getting rid of DFW.

## Requirements

- (VirtualBox)[https://www.virtualbox.org/wiki/Downloads]

- (Vagrant)[https://www.vagrantup.com/downloads.html]

## Getting Start

- Disable the Hyper-V

`Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All`

- Running Vagrant first time

`vagrant up`

- Access the Vagrant Virtual Machine created related to **vagrantfile**

`vagrant ssh`
