---
title: "4. Working With Data"
slug: working-with-data
date: 2021-06-18T00:25:03+01:00
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

Modern sites are data driven. This can be data stored in Markdown files or external APIs.

Hugo is not restricted to global configuration data, but can incorporate external data files, and also fetching data from remote resources.

<!--more-->

## Using Site Configuration Data in Your Theme

Just like layouts use ``{{ .Site.Title }}`` to access data from ``config.toml``, you can place all kinds of other data into the site's configuration file and use it.

Just add a new section, e.g. ``params``, to ``config.toml``:

```
[params]
	author = "Your Name"
```

and use in your layouts, e.g. ``partials/head.html``:

```
<meta name="author" content="{{ .Site.Params.author }}">
```

## Adding Google Analytics

Grab your Google Analytics tracking ID and add it to the site's configuration file:

```
googleAnalytics = "UA-xxxxxxxxxxx"
```

In ``themes/themename/layouts/parials/head.html`` use Hugo's build-in template

```
{{ template "_internal/google_analytics_async.html" . }}
```

NOTE: If you're using Google Analytics or other tracking software, be sure to consult local privacy laws, as you may need to obtain permission from your users to collect data.

## Populating Page Content Using Data in Front Matter

To make pages more data-driven, modify the archetype (e.g. ``archetypes/projects.md``):

```
---
title = "{{ replace .Name "-" " " | title }}"
draft: false
image: //via.placeholder.com/640.150
alt_text: "{{ replace .Name "-" " " | title }} screenshot"
summary: "Summary of {{ replace .Name "-" " " | title "
bullets:
- point 1
- point 2
---

Description of {{ replace .Name "-" " " | title }} site.
```

Notice that the name of the file is used to generate content for title, alt text, and even the main content.

Now, you can create new content with the associated archetype:

```
$ hugo new archetype/filename.md
```

You may have to refactor existing pages to reflect new frontmatter, but by doing so you can modify the themes ``single.html``, moving there common components, and keep everything consistent.

Edit ``themes/themename/layouts/projects/single.html``:

```
<section class="project">
	{{ .Content }}

	<img alt="{{ .Params.alt_text }}" src="{{ .Params.image }}">
</section>
```

* Notice that any custom field you added to front matter added to ``.Params`` collection by Hugo.
* Fields like ``description`` and ``title`` are [predefined fields](https://gohugo.io/content-management/front-matter/#predefined) by Hugo and don't need the ``params`` prefix.

However, there's nothing wrong not following this data-driven approach, but it may be more appropriate for thing that need to be more uniform.

Be aware that the added front matter is also available in other templates. Edit ``themes/themename/layouts/projects/list.html``:

```
{{ range .Pages }}

	<h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>

	<p>{{ .Summary }}</p>

{{ end }}
```

NOTE: You're not using ``params`` here. As you're iterating with ``range``, inside the block, ``range`` is pointing at the current entry, so you can access any of the properties of that item, including content or front matter data.

## Conditionally Displaying Data

You can add conditional logic to your layouts to control how to display data, e.g. by checking if a data field is set on page.

Hugo's ``isset`` function looks great, but has limitations: It doesn't handle situations where values are always defined but are empty, like default values. The ``description`` field is a default field, and the value will be defined, but could be empty if not set.

Handle this case by using Hugo's ``with`` function. As example edit ``themes/themename/layouts/partials/head.html``

```
<meta name="description" content="
	{{- with .Page.Description -}}
		{{ . }}
	{{- else -}}
		{{ .Site.Params.description }}
	{{- end -}}">
```

The ``with`` function rebinds the context and you can switch the current context to ``.Page.Description``.  The single period prints out the value. If the value of the context is empty, the block gets skipped, and you pair it with the block of an ``else`` statement.

Another case could be to show the site title on the home page, and a more specific on every other page. Again, edit ``partials/head.html``:

```
<title>
{{- if .Page.IsHome -}}
	{{ .Site.Title }}
{{- else -}}
	{{ .Title }} - {{ .Site.Title }}
{{- end -}}
</title>
```

## Using Local Data Files

The ``data`` folder can hold data files in YAML, JSON, or TOML formats that can be used in your layouts. In the layout you'll load the file and iterate over its contents.

Create a ``socialmedia.json`` in ``data``:

```
{
	"accounts": [
		{
			"name": "Twitter",
			"url": "https://twitter.com/username"
		},
				{
			"name": "LinkedIn",
			"url": "https://linkedin.com/in/username"
		}
	]
}
```

Content pages cannot include dynamic content, so you must use a layout to read the file and use it. With shortcodes you make function to include dyamic content in content pages. However, for now create a specific layout (instead of relying on the default ``single.html`` layout).

Create a new site layout ``layouts/_default/contact.html`` (you can incorporate it into the them if it's useful):

```
{{ define "main" }}
	<h2>Social Media</h2>

	<ul>
		{{ range .Site.Data.socialmedia.accounts }}
			<li><a href="{{ .url }}">{{ .name }}</a></li>
		{{ end }}
	</ul>
{{ end }}
```

As there's not archetype to associate the layout with content, you have explicitly assign the layout at the front matter of the content Markdown, e.g. ``content/contact.md``:

```
---
title:
date:
draft:
layout: contact
---

Contact Page

```


## Pulling Data from Remote Sources

You can also make API request with JSON responses. To access GitHub your repositories add this to ``config.toml`` at the ``params`` section:

```
[params]
	gh_url = "http://api.github.com/users"
	gh_user = "username"
```

Just like with local data files, create a new layout file ``themes/themename/layouts/_default/github.html``:

```
{{ define "main" }}

	{{ $url := printf "%s/%s/repos" .Site.Params.gh_url .Site.Params.gh_user }}

	{{ $repos := getJSON $url }}

	{{ range $repos }}
		<h2><a href="{{ .html_url }}>{{ .name }}</a></h2>
		<p>{{ .description }}</p>
	{{ end}}

{{ end }}
```

* Defines ``$url`` variable
* Us Go's ``printf`` to concatenate the base URL, user name, and ``/repos`` endpoint
* ``getJSON`` makes the request and fetches the JSON into a collection to be used with ``range``.

Every time you rebuild the site, Hugo makes a request to the GitHub API. If you don't want to hit the API every time you build, you can download the JSON data, store it in ``data``, and load it like local data.

With the layout set, you're ready to create a new content page:

```
$hugo new github.md
```

and ensure it uses the ``github`` layout:

```
---
title:
date:
draft:
layout: opensource
---

GitHub projects
```

You may want to pull the data from that site into another page, like a ``list.html``. To do so, you can use Hugo's ``GetPage`` function, which takes the path to the Markdown file, to pull data from any page into your layouts.

```
{{ with .Site.GetPage "/github.md" }}
	<h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
	<p>{{ .Summary }}</p>
{{ end }}
```

## Syndicating Content with RSS

Hugo creates RSS feeds for your site automatically using a build-in RSS 2.0 template. If you visit ``http://localhost:1313/index.xml`` you'll find a pre-build RSS feed that includes all of your pages.

Hugo generates RSS feeds for your sections too, und your categories have their own feed, e.g. for projects at ``http://localhost:1313/projects/index.xml``.

People won't know there's a feed unless you tell them. To make the feed discoverable, add a ``meta``tag to the ``partials/head.html``:

```
{{ range .AlternativeOutputFormats -}}
	{{- $link := `<link rel="%s" type="%s" href="%s" title="%s">` -}}
	{{- $title := printf "%s -%s" $.Page.Title %.Site.Title -}}

	{{- if $.Page.IsHome -}}
		{{ $title = $.Site.Title }}
	{{- end -}}

	{{ printf $link .Rel .MediaType.Type .Permalink $title | safeHTML }}
{{- end }}
```

This iterates over all alternative formats with the current page. There's just one, but you may add more in the future. Each content has a ``type`` attribute.

## Rendering Content as JSON

Hugo support JSON output out of the box, which means you can create a JSON API. Unlike RSS feeds, you need to create a layout for your JSON output, and you must specify which pages of your site should use this output type.

For your projects, create ``themes/themename/layouts/project/lists.json``:

```
{
	"projects": [
		{{- range $index, $page: = (where .Site.RegularPages "Type" "in" "project") }}
		{{- if $index -}} , {{-end }}
		{
			"url": {{ .Permalink | jsonify }},
			"title": {{ .Title | jsonify }]
		}
		{{- end }}
	]
}
```

Hugo won't generate the JSON until you configure it to do so. You can configure outputs format in the main configuration, but you can only specify that for the home page, all sections, and all content pages. To specify only a specific section, you specify it in the front matter of the section's page. For project, edit the ``content/project/_index.md`` and add ``outputs`` to the front matter:

```
outputs:
- HTML
- JSON
- RSS
```

Visit ``http://localhost:1313/projects/index.json``.

You can also change the ``url`` field in the page's front matter to change the URL for the page:

```
url: /projects.json
```

Unfortunately, Hugo will no longer the HTML page now. You have two options to fix this.

1. Configure the web server to rewrite the URL
2. Move the file before you upload it to your server - move ``projects/index.json`` to ``projects.json``. You can do this as a part of a larger build and deploy process.
