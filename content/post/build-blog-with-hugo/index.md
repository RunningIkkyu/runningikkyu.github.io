---
title: Make Your Own Blog with Hugo and GitHub Pages
date: 2022-03-06 00:00:00+0000
description: Make Your Own Blog with Uugo and GitHub Pages
slug: make-your-own-blog-with-hugo
image: cover.jpg
categories:
    - Blog
tags:
    - Hugo
    - Blog
    - Github Pagers
---

## Why hugo

- Easy.
- Fast.
- Popular.
- Support markdown.
- Github as your blog CMS.

## Install hugo

[Official Install Guide](https://gohugo.io/installation/)

Download the latest release from Hugo Github [release page](https://github.com/gohugoio/hugo/releases) and install on your machine.

> I've tried to build the hugo from source, but the latest version will be `v60`, while the latest
release version of hugo on the Github is `v110`, so I highly recommand you download the release pkg
from Github [release page](https://github.com/gohugoio/hugo/releases)!


## Select a theme for you blog

There're so many themes for you to choose on [Hugo Themes page](https://themes.gohugo.io/).

But too much themes without rates/stars lets me be dazzled. So I found a community ranking here: 

[awesome-hugo-themes](https://github.com/QIN2DIM/awesome-hugo-themes)

It sorts hugo themes by Github stars. 

I choose "[stack](https://github.com/CaiJimmy/hugo-theme-stack)" theme eventually for the following reason:

- I prefer the flatten style.
- It support floating TOC which is useful for long articles.
- Well-supported for comment system.
- Also support searching content.


## Set up hugo project

### Create a new site

Create a new site with hugo

```bash
hugo new site mynewsite
```

Init git

```
cd mynewsite && git init
```

### Setup your theme

Download the theme to your repo

```bash
git submodule add --depth 1 git@github.com:CaiJimmy/hugo-theme-stack.git themes/stack
```

Replace the config with example config file

```
rm config.toml && cp themes/stack/exampleSite/config.yaml config.yaml
```

### Add a post

Create a post by hugo:

```
hugo new posts/my-first-post.md
```


Paste these content and save:

```text
---
title: My first post
date: 2022-01-01 00:00:00+0000
description: Hello world
slug: my-first-post
categories:
    - Blog
tags:
    - Hello
    - World
---
```


## Start the server

```
hugo server -D --bind=0.0.0.0
```

`--bind=0.0.0.0` will make the site public, which is useful when you're developing on a cloud
server without GUI.


## Add Comment system

The "stack" theme supports many [comment systems](https://stack.jimmycai.com/config/comments). 

