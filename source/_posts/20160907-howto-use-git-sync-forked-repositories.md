---
title: How to use Git to sync forked repositories
date: 2016-09-07 21:41:00
categories:
  - HOWTO
tags:
  - fork
  - git
  - github
  - gitlab
  - repository
---

#### Overview

This article describes how to use `git` to sync forked repositories.

#### Background

I frequently need to look up the exact series of commands needed to sync with an upstream repository. This article is primarily for my convenience, but may be useful to others as well.

<!-- more -->

#### Fork

Fork the repository by clicking **[ <nop class="fa fa-code-fork"> Fork ]** from your source code repository website. We'll use `SOME-REPO`, in this example.

#### Clone

Create a local clone of your fork and configure `git` to sync your fork with the original:

```` bash
$ git clone https://github.com/YOUR-USERNAME/SOME-REPO
$ git remote add upstream https://github.com/ORIGINAL-USER/SOME-REPO
````

#### Contribute

Hack on code in your fork; make <nop class="fa fa-github"> Pull Requests / <nop class="fa fa-gitlab"> Merge Requests.

#### Sync

Sync your fork to keep it up-to-date with the upstream repository:

```` bash
$ git fetch origin -v
$ git fetch upstream -v
$ git merge upstream/master
````

#### Simplify

Assign a `git` alias to perform the sync steps for you:

```` ini ~/.gitconfig
[alias]
  pu = !"git fetch origin -v; git fetch upstream -v; git merge upstream/master"
````

Usage:

```` bash
$ git pu
From https://github.com/YOUR-USERNAME/SOME-REPO
 = [up to date]      master     -> origin/master
From https://github.com/ORIGINAL-USER/SOME-REPO
 = [up to date]      master     -> upstream/master
Already up-to-date.
````

#### Summary

Perform the **Fork** & **Clone** steps once for each forked repository. **Contribute** regularly. **Sync** often.

((( <nop class="fa fa-glass"> - Party like a rock star! - <nop class="fa fa-music"> )))

#### References

<nop class="fa fa-github"> | Github Bootcamp / [Fork A Repo](https://help.github.com/articles/fork-a-repo/)
<nop class="fa fa-github"> | Github Guides / [Forking Projects](https://guides.github.com/activities/forking/)
<nop class="fa fa-gitlab"> | Gitlab / [How to fork a project](http://docs.gitlab.com/ce/gitlab-basics/fork-project.html)
