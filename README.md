# 4-20ma.io

## Generate

Create a new post/page

```` bash
$ hexo new post "My new post"
$ hexo new page "My new page"
````

Moves a draft post from _drafts to _posts folder

```` bash
$ hexo publish "My draft post"
````

Removed generated files and cache

```` bash
$ hexo clean
````

Generate static files

```` bash
$ hexo generate
````

Start the server

```` bash
$ hexo server
````

## Deploy

Deploy website

```` bash
$ hexo deploy
````

...OR...

Deploy website after generation

```` bash
$ hexo generate --deploy
````

## Info

Display version information

```` bash
$ hexo version
hexo: 3.2.2
hexo-cli: 1.0.2
os: Darwin 15.6.0 darwin x64
http_parser: 2.7.0
node: 6.5.0
v8: 5.1.281.81
uv: 1.9.1
zlib: 1.2.8
ares: 1.10.1-DEV
icu: 57.1
modules: 48
openssl: 1.0.2h
````

List the information of the site

```` bash
$ hexo list
````

Get help on a command

```` bash
$ hexo help
````


## Configuration

### Main

Modify `_config.yml`

``` bash
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: "{ url: '4-20ma.io' }"
subtitle:
description: Miscellaneous posts related to hardware / software development and industrial process control.
author: Doc Walker
language: en
timezone: US/Central

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: https://4-20ma.io
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :year:month:day-:title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 1
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: alpha-dust # fav #1
# theme: very-simple # fav #2
# theme: landscape
# theme: light
# theme: phase
# theme: freemind # ugly
# theme: corporate # too corporate

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/4-20ma/4-20ma.github.io.git
```

### Domain

Modify `public/CNAME`:

```` bash
4-20ma.io
````

NOTE: Ensure this domain matches that defined in `_config.yml/site.url`.

## License

````
Copyright 2016 Doc Walker

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
````
