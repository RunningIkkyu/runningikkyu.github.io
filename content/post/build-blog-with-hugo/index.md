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

There're two **open source** comment system that I prefered: 

- utterance
- [giscus](https://giscus.app/)


`giscus` is a comment system based on Github Discussions, while `utterance` is based on github issues. 
For me, Github Discussions is a perfect place to hold all comments for blog.
Finnally I choose `giscus` for my blog's comment system.

Steps to config `giscus` as your comment system:

- Make the repository public.
- Install the [**giscus**](https://github.com/apps/giscus) app on your repo.
- [Turn on the Discussions feature](https://docs.github.com/en/github/administering-a-repository/managing-repository-settings/enabling-or-disabling-github-discussions-for-a-repository) for your repository.

After these settings, you need to config giscus on your hugo project:


Fill all options on [giscus](https://giscus.app/) site, you'll get a script tag like this:

```html
<script src="https://giscus.app/client.js"
        data-repo="repo"
        data-repo-id="repo-id"
        data-category="Announcements"
        data-category-id="categorie_id"
        data-mapping="pathname"
        data-strict="1"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="top"
        data-theme="preferred_color_scheme"
        data-lang="en"
        data-loading="lazy"
        crossorigin="anonymous"
        async>
</script>
```

Let's convert that into `config.toml`:

```toml
[params.comments]
enabled = true
provider = "giscus"

[params.comments.giscus]
reactionsEnabled = 1
emitMetadata = 0
repo = "repo"
repoID = "repo-id"
category = "Announcements"
categoryID = "categorie_id"
mapping = "pathname"
strict=true
inputPosition = "top"
lang="en"
loading="lazy"
theme="preferred_color_scheme"
```


Start the server and you'll see the comment widgets on the bottom of your posts:

```
hugo server -D --bind=0.0.0.0
```
