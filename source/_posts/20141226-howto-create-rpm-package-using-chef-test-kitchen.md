---
title: >-
  How to create an RPM package using Chef, Test Kitchen
date: 2014-12-26 16:48:00
categories:
  - HOWTO
subcategories:
  - Create RPM
tags:
  - centos
  - chef
  - fcgiwrap
  - git
  - parallels
  - postfix
  - rhel
  - rpm
  - ruby
  - test-kitchen
  - vagrant
  - virtualbox
---

This post describes how to leverage Chef and Test Kitchen to create a pristine virtual machine from which to create an RPM package.

#### Background

I needed customized versions of the **FcgiWrap** and **Postfix** RPM packages and preferred to develop a method that would allow me to periodically update the packages as new versions of the upstream source were released. Vagrant is a great tool for managing virtual machines and I was originally going to use this to provision a new VM to build the packages. I developed Chef cookbooks to provision the VMs, and while developing integration tests for the provisioners, I realized that it was more effective to use Test Kitchen to build and test my VMs (which itself uses Vagrant).

<!-- more -->

#### Prerequisites

The following are required:

- Git (v2.2.1 used)
- Ruby (v2.1.5 used)
- Chef (v11.16.4 used)
- Test Kitchen (v1.2.1 used)
- Vagrant (v1.6.5 used)
- Virtual machine (Parallels 10.0.0 used, but VirtualBox works as well)

#### Example / FcgiWrap

Clone the repository and use `kitchen` to converge the node:

```` bash
$ git clone https://github.com/4-20ma/cookbook-fcgiwrap_rpm
$ cd cookbook-fcgiwrap_rpm
$ bundle exec kitchen converge
...
$ tree .products/
.products/
└── fcgiwrap-1.1.0-1.el6.x86_64.rpm
````

You can now transfer the `.rpm` file to the target machine(s) and install via `rpm` or `yum`.

#### Example / Postfix

Clone the repository and use `kitchen` to converge the node:

```` bash
$ git clone https://github.com/4-20ma/cookbook-postfix_rpm
$ cd cookbook-postfix_rpm
$ bundle exec kitchen converge
...
$ tree .products/
.products/
├── postfix-2.11.1-0.el6.x86_64.rpm
└── postfix-perl-scripts-2.11.1-0.el6.x86_64.rpm
````

You can now transfer the `.rpm` file to the target machine(s) and install via `rpm` or `yum`.

#### Summary

Test Kitchen is not only effective at performing integration testing for a Chef cookbook, it is also useful to spin up a pristine virtual machine to perform tasks such as building an RPM package.

((( <span class="fa fa-glass"> - <span class="fa fa-music"> )))

####  References

Cookbook Sources:

- <span class="fa fa-github"> [4-20ma](https://github.com/4-20ma) / [FcgiWrap RPM Cookbook](https://github.com/4-20ma/cookbook-fcgiwrap_rpm) – builds FcgiWrap RPM
- <span class="fa fa-github"> [4-20ma](https://github.com/4-20ma) / [Postfix RPM Cookbook](https://github.com/4-20ma/cookbook-postfix_rpm) – builds Postfix RPM

3rd party software used (alphabetical):

- [Chef](https://www.chef.io)
- <span class="fa fa-github"> [schnell18](https://github.com/schnell18) / [FcgiWrap Source](https://github.com/schnell18/fcgiwrap)
- <span class="fa fa-git-square"> [Git](https://git-scm.com)
- [Parallels](http://www.parallels.com)
- [Postfix](http://www.postfix.org)
- [Ruby](https://www.ruby-lang.org/en/)
- [Test Kitchen](http://kitchen.ci)
- [Vagrant](https://www.vagrantup.com)
- [VirtualBox](https://www.virtualbox.org)
