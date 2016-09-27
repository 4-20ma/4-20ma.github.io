---
title: >-
  How to add GitHub Pages to a project
date: 2013-01-02 08:16:00
categories:
  - HOWTO
tags:
  - gh-pages
  - git
  - github
---

#### Overview

GitHub Pages is a static site hosting service and is designed to host personal, organization, or project pages directly from a GitHub repository.

#### Background

I occasionally need to add GitHub Pages (gh-pages) to a project. These instructions are based on a GitHub help [article](https://help.github.com/articles/creating-project-pages-from-the-command-line/) and have been customized for my use.

<!-- more -->

#### Steps

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

((( <span class="fa fa-glass"> - Enjoy responsibly. - <span class="fa fa-music"> )))

#### References

<span class="fa fa-github"> | GitHub Help / [GitHub Pages Basics](https://help.github.com/categories/github-pages-basics/)
<span class="fa fa-github"> | GitHub Help / [Creating Project Pages from the command line](https://help.github.com/articles/creating-project-pages-from-the-command-line/)
