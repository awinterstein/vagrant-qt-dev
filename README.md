Vagrant Qt-Development
======================

This repository contains a Vagrant file and an Ansible playbook for creating a virtual machine for the development of Qt applications. Compiler and tools for Android as a target platform can be installed optional.

## Requirements

* Vagrant >= v1.8
* Ansible >= v2.4
* Virtualbox >= v5

## Usage

Copy the file `playbook.yml.example` to `playbook.yml` and adapt the content to your needs. Especially the variables `USERNAME` and `USERMAIL` have to be set to the values that should be used for Git commits.

Just run `vagrant up` then in the directory where the `Vagrantfile` is placed and wait for the machine to become ready and being provisioned.
