---
title: "Building a Theme (2/6)"
date: 2021-06-18T00:19:58+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
series: Static Websites with Hugo
categories:
- Web
tags:
- Hugo
---

With themes you set how the website looks. Of course you can just use one of many Hugo themes, but sometimes you have to build a theme yourself.

<!--more-->

A basic Hugo theme only needs these files:

```
layouts/
|--- _default
|  --- list.html
|  --- single.html
|--- index.html
```

* **index.html** is the home page of the site
* **default** contains the default layouts applied to single content pages (``single.html``) and lists of content pages (``list.html``). However, there are more Hugo templates.

## Generate a theme

Use Hugo's build-in theme generator to set up a theme structure:

```
$ hugo new theme themename
```

This creates a theme with following structure:

```
themes/themename/
|--- archetypes/
|   --- default.md
|--- layouts/
|   --- _default/
|      --- baseof.html
|      --- list.html
|      --- single.html
|   --- partials/
|      --- footer.html
|      --- head.html
|      --- header.html
|   --- 404.html
|   --- index.html
|--- static/
|   --- css/
|   --- js/
|--- LICENSE
|--- theme.toml
```

Note, that there's already a ``layouts/_default`` directory with single, list, and homepage layout. However, they're empty, and you should move your existing layouts here.

You also have to tell Hugo to use the theme by adding to following to ``config.toml``:

```
theme = "themename"
```

## Using Content Blocks and Partials

Breakup the HTML skeleton into reusable chunks. With ``themes/themename/layouts/_default/baseof.html`` Hugo provides a single place to put your skeleton that all other layouts can build upon. Instead of including the full skeleton, it's pulling in other files, or *partials*, which contain pieces of layout. Placing common pieces in partials makes it easier for reuse across different layouts, and helps thinking about parts of your site as components.

The first partial is ``head.html`` which contains what appears in the ``head`` section of a website, e.g.:

```
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{{ .Site.Title }}</title>
</head>
```

Likewise, the ``header.html`` contains what appears in the ``header`` section, e.g. navigation:

```
<header>
  <h1>{{ .Site.Title }}</h1>
</header>

<nav>
  <a href="/">Home</a>
  <a href="About"></a>
  <a href="Work"></a>
  <a href="Life"></a>
  <a href="Contact"></a>
</nav>
```

And so the ``footer.html`` partial contains the ``footer`` section (here, using Go's date formatting; Mon Jan 2 15:04:05 MST 2006):

```
<footer>
  <small>Copyright {{ now.Format "2006" }} Me.</small>
</footer>
```

Partials in the ``baseof.html`` look like this:

```
{{- partial "head.html" . -}}
```

* ``{{-`` suppresses whitespace character in the output. Placing the dash after the opening braces removes all whitespace in front of the expression
* ``-}}`` placing the dash in front of the closing braces remove whitespace after the expression.
* The ``partial`` function takes a filename and a context for the data. The dot (``.``) passes "the current context" to the partial, which enables to access data like page title or content. The Page context will be available to the partial.

The line ``{{- block "main" . }}{{- end }}`` looks for a block named "main" and pulls in the template. Those blocks are what to define in your actual layout pages like ``index.html`` and ``single.html``.

To define this block in your home page, modify ``themes/basic/layouts/index.html`` like this:

```
{{ define "main" }}

	{{ .Content }}

{{ end }}
```

As the ``index.html`` layout affect the site's home page only, also modify code in ``themes/themename/layouts/_default/single.html`` in the same way.

## Styling the Theme with CSS

Create a new stylesheet file at ``themes/themename/static/css/style.css``.

Now you can style the elements of the template as usual.

In the ``head.html`` add a link tag to load the stylesheet:

```
<link rel="stylesheet" href="{{ "css/style.css" | relURL }}">
```
