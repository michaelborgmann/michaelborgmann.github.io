---
title: "Adding Content Sections (3/6)"
date: 2021-06-18T00:23:00+01:00
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

When creating new pages, the archetype acts as a content template, filling in YAML front matter. Just create more specific archetypes for other types of content, and include whatever you'd like, including placeholder content.

<!--more-->

## Creating New Archetype

Create a new Mardown file in the ``archetypes`` folder, e.g.:

* ``projects.md``

Add some front matter at the top of the Markdown file:

```
---
title: "{{ replace .Name "-" " "| title }}"
draft: false
---
```

Add some placeholder content; use [Markdown syntax](https://www.markdownguide.org/basic-syntax/).

Placeholder Images
```
![alt](//via.placeholder.com/640x150)
```

## Create New Content Page

Whenever you create a new content page, reflecting an archetype, Hugo generates the new content file using the archetype as basis.

```
$ hugo new archetype/content.md
```

*If you created an archetype for projects, and you want to create a new page for a project: ``hugo new project/projectname.md``

Replace the placeholder text with proper content.

## Creating List Layout

Beside of single pages, a common need for websites is to show collections of pages like a directory, which can be done in Hugo with *list layouts* named ``list.html``.

After creating a new theme (and some pages) the ``_default/list.html`` is blank, and if you want to see the collection of pages (e.g. ``http://localhost:1313/projects``) you just see an empty page.

Let's create a generic ``themes/themename/layouts/_default/list.html``:

```
{{ define "main" }}

  <h2>{{ .Title }}</h2>

  <ul>
    {{ range .Pages }}
      <li>
        <a href="{{ .RelPermalink }}">{{ .Title }}</a>
      </li>
    {{ end }}
  </ul>

{{ end }}
```

* At ``{{ range .Pages }}`` the ``.Pages`` collection contains all of the pages related to the section. Hugo collects all pages within a content category (e.g. ``content/projects``) and makes them in the ``.Pages`` variable in the context available.
* The ``range`` function iterates over the result, and makes every record of the collection available.
* Inside of the ``range``block, you can access the properties of a page, as the context is set to that specific page.

## Creating More Specific Layouts

Some pages or section of a site want to have different themes or layouts, e.g. a sidebar.

Add a new folder to ``themes/themename/layouts`` (e.g. ``projects``). Add a ``single.html`` to it and define the ``main``block:

```
{{ define "main" }}

	<h2>Specific Layout Template</h2>

{{ end }}
```

As the ``.Pages`` variable is not accessible in single pages, but if you still want to show a page collection, Hugo provides a mechanism to access any content collection. ``.Site.RegularPages`` gives access to all pages of your site, and you can filter it down with the ``where`` function:

```
<ul>
	{{ range (where .Site.RegularPages "Type" "in" "projects") }}

		<li>
			<a a href="{{ .RelPermalink }}>{{ .Title }}</a>
		</li>

	{{ end }}
</ul>
```

You can sort items too, by most recents with ``.ByDate`` and reverse with ``.Reverse``:

```
range (where .Site.RegularPages "Type" "in" "projects").ByDate.Reverse
```

or to just show the most recent item, e.g. to showcase on the homepage:

```
range first 1 (where .Site.RegularPages "Type" "in" "projects").ByDate.Reverse
```

## Adding Content to List Pages

When visiting a list page you basically see the rendered output of the ``list.html``, but you can also add content to the page as well.

To add content to list pages, add an ``_index.md`` file to the folder associated with the content (collection can be ``projects``):

```
$ hugo new collection/_index.md
```

The file should contain filled in front matter and placeholder content from the associated archetype (e.g. ``project.md``).

Don't forget to add code to include the content - ``{{ .Content }}`` - into the template ``themes/themename/layouts/_default/list.html``.
