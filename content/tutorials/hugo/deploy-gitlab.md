---
title: "6. Deploy on Gitlab"
slug: deploy-on-gitlab
date: 2021-06-18T00:28:41+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
sidebar:
- "[1. Setup Hugo](/tutorials/hugo/setup-hugo/)"
- "[2. Building a Themes](/tutorials/hugo/building-a-theme/)"
- "[3. Adding Content Sections](/tutorials/hugo/adding-content-sections/)"
- "[4. Working with Data](/tutorials/hugo/working-with-data/)"
- "[5. Add Blogging](/tutorials/hugo/add-blogging/)"
- "[6. Deploy on GitLab](/tutorials/hugo/deploy-on-gitlab/)"
---

Deploy a Hugo static page on GitLab.

<!--more-->

## Create GitLab Project

Create a new project on GitLab and choose a project name similar to ``sitename.gitlab.io``

## Update config.toml

Change the base url in the ``config.toml`` to reflect your site name: ``baseurl = "https://sitename.gitlab.io"``

## Add .gitlab-ci.yml

Add a ``.gitlab-ci.yml`` to your project root and add this content:

```
image: registry.gitlab.com/pages/hugo:latest

variables:
  GIT_SUBMODULE_STRATEGY: recursive

pages:
  script:
  - hugo
  artifacts:
    paths:
    - public
  only:
  - master
```

## Push Your Hugo to GitLab

Put you local Hugo site und Git version control, and add a ``.gitignore``:

```
# exclude js dependencies
node_modules

# exlude Hugo's output
public
```
