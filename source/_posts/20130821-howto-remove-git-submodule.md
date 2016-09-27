---
title: >-
  How to remove a Git submodule
date: 2013-08-21 20:18:00
categories:
  - HOWTO
subcategories:
  - Remove Git Submodule
tags:
  - git
  - submodule
TODO:
  - Confirm whether `git submodule deinit` performs the desired .git/config edit?
---

#### Overview

{% blockquote Scott Chacon and Ben Straub https://git-scm.com/book/en/v2/Git-Tools-Submodules Pro Git %}
It often happens that while working on one project, you need to use another project from within it. Perhaps it’s a library that a third party developed or that you’re developing separately and using in multiple parent projects. A common issue arises in these scenarios: you want to be able to treat the two projects as separate yet still be able to use one from within the other.
{% endblockquote %}

#### Background

I frequently need to look up the exact series of commands remove a git submodule. This post is primarily for my convenience, but may be useful to others as well.

<!-- more -->

#### Modify

Remove the relevant `submodule` section from each of the following files:

```` ini .gitmodules
...
[submodule "vendor"]
  path = vendor
  url = git://github.com/some-user/some-repo.git
...
````

```` ini .git/config
...
[submodule "vendor"]
  url = git://github.com/some-user/some-repo.git
...
````

#### Commit

  1. Stage changed `.gitmodules` file
  1. Unstage and remove submodule path from the index (don’t include a trailing slash – that will lead to an error)
  1. Remove submodule files from index
  1. Commit the changes
  1. Remove submodule files

```` bash
$ git add .gitmodules
$ git rm --cached path/to/submodule
$ rm -rf .git/modules/submodule_name
$ git commit
$ rm -rf path/to/submodule
````

#### Summary

Removing a submodule can be a tedious task, but can be accomplished by following the tasks in this post.

((( <span class="fa fa-glass"> - Enjoy your lighter repository. - <span class="fa fa-music"> )))

#### References

<span class="fa fa-git-square"> | Git Reference / [git-submodule](https://git-scm.com/docs/git-submodule)
<span class="fa fa-git-square"> | Pro Git > Git Tools / [Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
<span class="fa fa-external-link"> | David Walsh / [Remove a Submodule](https://davidwalsh.name/git-remove-submodule)
