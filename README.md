lamp-default
============

A default LAMP stack built on Debian Wheezy (7) running Apache 2.4 and PHP 5.5.

## Prerequisites

In order to get started you must have Vagrant installed for VM management and Ansible for VM provisioning. Vagrant can be downloaded from the [Vagrant website](http://www.vagrantup.com/). If you haven't installed Ansible, you can learn about it in [Installation &mdash; Ansible Documentation](http://docs.ansible.com/intro_installation.html).

## Setup

Once Vagrant and Ansible are successfully installed you can start on setting up this environment. First you need to clone this repository to wherever your workspace is located.

```
$ git clone git@github.com:TotalActiveMedia/lamp-default.git ~/projects/vagrant/lamp-php55
```

Then you need to initialize the Git submodules which contain Ansible roles for Apache, MySQL and PHP.

```
$ git submodule init
$ git submodule update
```

Once this is done you can run ```vagrant up```.