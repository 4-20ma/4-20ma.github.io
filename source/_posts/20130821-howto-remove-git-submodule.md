---
title: >-
  How to remove a git submodule
date: 2013-08-21 20:18:00
categories:
  - HOWTO
subcategories:
  - Remove Git Submodule
tags:
  - git
---

This is an excellent article describing how to [remove a git submodule](https://davidwalsh.name/git-remove-submodule).

Short version below (in case original disappears):

- Delete the relevant section from the `.gitmodules` file

```` git .gitmodules
...
[submodule "vendor"]
  path = vendor
  url = git://github.com/some-user/some-repo.git
...
````

- Stage the changes

```` bash
$ git add .gitmodules
````

- Delete the relevant section from `.git/config` file

```` git .git/config
...
[submodule "vendor"]
  url = git://github.com/some-user/some-repo.git
...
````

- Clean up

  1. Unstage and remove submodule path from the index (don’t include a trailing slash – that will lead to an error)
  1. Remove submodule files from index
  1. Commit the changes
  1. Remove submodule files

```` bash
$ git rm --cached path/to/submodule
$ rm -rf .git/modules/submodule_name
$ git commit
$ rm -rf path/to/submodule
````
