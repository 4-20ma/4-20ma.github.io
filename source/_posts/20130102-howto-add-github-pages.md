---
title: >-
  How to add Github Pages to a project
date: 2013-01-02 08:16:00
categories:
  - HOWTO
tags:
  - git
  - github
  - gh-pages
---

I occasionally need to add Github Pages (gh-pages) to a project. These instructions are based on a Github help [article](https://help.github.com/articles/creating-project-pages-from-the-command-line/) and have been customized for my use.

Create orphan `gh-pages` branch in `doc/html` directory:

```` bash
$ cd doc/html
$ git init
$ git remote add origin `git config --file ../../.git/config remote.origin.url`
$ git checkout --orphan gh-pages
$ git rm -rf .
````

Create initial commit:

```` bash
$ touch index.html
$ git add .
$ git commit -m 'Initial commit'
````

Configure `gh-pages` branch:

```` bash
$ git config branch.gh-pages.remote origin              # optional
$ git config branch.gh-pages.merge refs/heads/gh-pages  # optional
$ git push origin gh-pages
````

Enjoy responsibly.
