---
title: "5. Add Blogging"
slug: add-blogging
date: 2021-06-18T00:27:24+01:00
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

To add a blog to a Hugo site create a new content type and and layouts to support displaying posts.

<!--more-->

Start creating an archetype for posts and create ``archetypes/posts.md``:

```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: false
author: Your Name
---

Lorem ipsum dolor sit amet,

<!--more-->

consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
```

The ``<!--more-->`` line specifies where the content summary ends, to be used with ``{{ .Summary }}``. Sometimes the auto-generated summary ends at an unwanted place. To control this add ``<!--more-->``.

Now you're ready to generate content for a post:

```
$ hugo new posts/post.md"
```

## Creating the Post's Layout

Pimp up the bare bare post by creating a new layout for the post at ``themes/themename/layouts/posts/single.html``:

```
{{ define "main" }}

<article class="post">

  <header>
    <h2>{{ .Title }}</h2>
    <p>By {{ .Params.Author }}</p>
    <p>Posted {{ .Date.Format "January 2,2006" }}</p>
    <p>Reading time: {{ math.Round (div (countwords .Content) 200.0) }} minutes.</p>
  </header>

  <section class="body">
    {{ .Content }}
  </section>

</article>

{{ end }}
```

## Syntax Highlighting for Code

Add Pygments-style at ``config.toml``:

```
pygmentsUseClasses = true
```

Then generate a stylesheet to highlight your code:

```
$ hugo gen chromastyles --style=github > syntax.css
```

Add the ``syntax.css`` style to your ``head.html`` partial.

Now you can use code syntax highlighting:

```javascript
let x = 25;
let y = 30p
```

## Organizing Content with Taxonomies

To organize blogs many categorize posts and apply tags. This logical grouping of content is known as *taxonomy*. Hugo supports categories and tax out of the box, and can generate category and tag list pages automatically. All you have to do is add categories and tags to your front matter; edit ``archetypes/posts.md``:

```
categories:
- Development
tags:
- iOS
```

However, this change will not affect already created content, and you have to add categories and tags there too.

You can visit [http://localhost:1313/tags](http://localhost:1313/tags) and [http://localhost:1313/categories](http://localhost:1313/categories).

To customize the page that displays the list of all your tags, create a new layout named ``tag.terms.html`` inside ``themes/themename/layouts/_default``:

```
{{ define "main" }}

  {{ range .Data.Terms.Alphabetical }}

    <p class="tag">
      <a href="{{ .Page.Permalink }}">{{ .Page.Title }}</a>
      <span class="count">({{ .Count }})</span>
    </p>

  {{ end }}

{{ end }}
```

Add the usual layout boilerplate, but instead of iterating of the related pages, iterate over all of the tags for the site with ``.Data.Terms``. This will give you access to the number of content pages associated with each tag.

When watching your site's ``tags``, Hugo will look at ``content/tags/_index.md`` for content, so let's create it:

```
$ hugo new tags/_index.md
```

and add some content:

```
---
title: "Tags"
date: 2021-06-14T15:58:34+01:00
draft: false
---
```

You can also add the list of tags to the post's single layout. Edit ``themes/themename/layouts/posts/single.html``, and it after showing the posting date:

```
Posted {{ .Date.Format "January 2,2006" }}
<span class="tags">
in
{{ range .Params.tags }}
  <a class="tag" href="/tags/{{ . | urlize }}">{{ . }}</a>
{{ end }}
</span>
```

Of course you can style the tags as well, by adding this to your stylesheet:

```
a.tag {
  background-color: #ddd;
  color: #333;
  display: inline-block;
  padding: 0.1em;
  font-size: 0.9em;
  text-decoration: none;
}
```

## Disabling Taxonomies

by default, Hugo generates category and tag pages. If you don't want them, you can configure the site to ignore them. In ``config.toml`` add:

```
[taxonomies]
  category = "categories"
```

This defines taxonomies to exclude tags. If you want tags but no categories:

```
[taxonomies]
  tag = "tag"
```

If you don't want any kind of taxonomy:

```
disableKinds = ["taxonomy", "taxonomyTerm"]
```

## Customizing the URL for Posts

By default the blog contents show up under ``posts/``, e.g. ``http://localhost:1313/posts/first-post``.

Many blogs use the year/month/title format.

A *permalink* is a permanent link to a specific page, which can be used to share a page.

Hugo lets you define how to structure links in ``config.toml``:

```
[permalinks]
  posts = "posts/:year/:month/:slug/"
```

The *slug* identifies the page's content, and is generated front the page title by default, but can be defined in the front matter.

Unfortunately Hugo doesn't support generating ``posts/2020`` automatically, but there's a workaround with taxonomies.

Add a ``year``and ``month`` field to the front matter of a post:

```
year: "2020"
month: "2020/01"
```

Of course you can also add the date to ``archetypes/posts.md`` and generating the date when creating a new post:

```
year: "{{ dateFormat "2006" .Date}}"
month: "{{ dateFormat "2006/01" .Date}}"
```

Next, define the permalinks for ``year`` and ``month`` pages at ``config.toml``:

```
posts = "posts/:year/:month/:slug"
year = "/posts/:slug"
month = "/posts/:slug"
```

To generate the archive list, define year and month data as new taxonomies, also at ``config.toml``:

```
[taxonomies]
  year = "year"
  month = "month"
  tag = "tags"
  category = "categories"
```

When you define a taxonomies section, it replaces the default.

Now, you can visit your posts as ``/posts/<year>`` or ``/posts/<year>/<month>``

## Customize Blog List Pages

You can also create a list for blog posts to make it more appealing, as it's using the default layout otherwise.

Create a partial to hold the bulk of markup for the post and share it across layouts. Add ``themes/themename/layouts/partials/post_summary.html``:

```
<article>
  <header>
    <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
    <time>
      {{ .Date | dateFormat "January" }}
      {{ .Date | dateFormat "2" }}
    </time>
  </header>

  {{ .Summary }}

</article>
```


Next create a layout to use the partial iterating over the pages and displaying them; create ``themes/themename/layouts/posts/lists.html``:

```
{{ define "main" }}

  <h2>{{ .Title }}</h2>

  {{ range .Pages }}
    {{ partial "post_summary.html" . }}
  {{ end }}

{{ end }}
```

This works for posts, but not for taxonomy pages as year and month. To make it work you have to specify more specific layouts. To speed up for year and month, just copy the ``posts/lits.html``:

```
$ cp posts/list.html _defaylt/year.html
$ cp posts/list.html _default/month.html
```

## Add Pagination

Hugo has build-in pagination, and it's enabled by default. All you have to do is change how to fetch pages and add pagination navigation to your layouts.

To use pagination, use ``.Paginator.Pages`` instead of ``.Pages`` in your range statement, like: ``{{ range .Paginator.Pages }}``

Hugo shows by default 10 pages, what can be overriden.

Use ``layouts/posts/list.html`` as base to create a new template at ``layouts/posts/list_with_pagination.html``:

```
{{ define "main" }}

  <h2>{{ .Title }}</h2>

  {{ range (.Paginator 5).Pages }}
    {{ partial "post_summary.html" . }}
  {{ end }}

  {{ template "_internal/pagination.html" . }}

{{ end }}
```

As it's not so pretty, consider styling it:

```
.pagination {
  display: flex;
  justify-content: space-between;
  list-style: none;
  margin: 1 em auto;
  padding: 0;
}

@media only screen and (min-width: 768px) {
  .pagination{
    width: 30%;
  }
}

.pagination > .page-item {
  border: 1px solid #ddd;
  flex: 1;
  text-align: center;
  width: 5em;
}

.pagination .page-link {
  display: block;
  color: #000;
  text-decoration: none;
}

.pagination > .page-item.active {
  background-color: #333;
}

.pagination > .page-item.active > .page-link {
  color: #fff;
}

.pagination > .page-item.disabled > .page-link {
  color: #ddd;
}
```

You can also change the number of pages to default ``{{ range .Paginator.Pages }}``, and specify it in the ``config.toml`` with ``Paginate = 10``.

## Adding comments to Posts Using Disqus

Create a new account on Disqus for your site, and configure it.

Take the Disqus shortname to configure it for use in ``config.toml``:

```
disqusShortame = "disqus-shortname"
```

Now, open ``layouts/posts/single.html`` and add a new comment section (after the body section) that uses Hugo's build-in Disqus template.

```
  <section class="comments">
    <h3>Comments</h3>
    {{ template "_internal/disqus.html" . }}
  </section>
```

As Disqus won't load on sites server fron localhost, use a tunneling service and its client to proxy connections through external servers:

```
$ npx localtunner -p 1313
```

This downloads the localtunnel package and executes its binary. Use the URL seen in the terminal to visit the page.

Commenting is enabled by default. If you want to turn comments off, disable commenting in the front matter of a post:

```
disableComments: true
```

Then modify the post layout to use this value to determine whether or not the comments should be displayed; modify the comments section at ``layouts/posts/single.html``:

```
  <section class="comments">
    <h3>Comments</h3>
    {{ if .Params.disableComments }}
      <p>Comments are disabled for this post</p>
    {{ else }}
      {{ template "_internal/disqus.html" . }}
    {{ end }}
  </section>
```

## Display Related Content

To show some related content, you have to add keywords to your front matter

XXX *this section is omitted*
