---
title: "Static Pages (5/10)"
date: 2021-06-18T10:41:02+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
series: Getting MEAN
categories:
- Web
tags:
- MEAN
---

*Building a static site with Node and Express I*

Before building a dynamic Angular powered web app, let's go through static pages with Express, featuring [Bootstrap](https://getbootstrap.com) and [Pug](https://pugjs.org). Furthermore, decoupling data from static pages into controllers already prepares you to build a database feeded dynamic web page.

<!--more-->

## Define routes in Express

When planning your web app it likely involves more than one page, and the transition between pages - this defines your UX flow.

When thinking about your routes, map the pages to an URL path, and consider grouping some of them into collections. As example:

| Collection | Page | URL Path |
|:--|:--|:--|
| Articles | Article list | `/` |
| Articles | Read article | `/articles/id`
| Articles | Add article | `/articles/add`
| About | About page | `/about` |

Given this example you would create two different controllers: Articles and About.

X Creating Routes (NOTE: Code may be unneeded)

Based on your URL path mapping, build the new routes first. For this example you would add two new route files: `routes/articles.js`:

```
var express = require('express');
var router = express.Router();

router.get('/', function (req, res) {
  res.send('NOT IMPLEMENTED: Article list');
})

router.get('/:articleid', function (req, res) {
  res.send('NOT IMPLEMENTED: Article');
})

router.post('/add', function (req, res) {
  res.send('NOT IMPLEMENTED: Add article');
})

module.exports = router;
```

and `routes/about.js`:

```
var express = require('express');
var router = express.Router();

router.get('/', function (req, res) {
  res.send('NOT IMPLEMENTED: Article list');
})

module.exports = router;
```

X Create Controllers

First, create your controllers. Add `controllers/articleController.js`:

```
exports.article_list = function(req, res) {
    res.send('NOT IMPLEMENTED: Article list');
};

exports.article_read = function(req, res) {
    res.send('NOT IMPLEMENTED: Article');
};

exports.article_write = function(req, res) {
    res.send('NOT IMPLEMENTED: Add article');
};
```

and `controllers/aboutController.js`:

```
exports.about = function(req, res) {
    res.send('NOT IMPLEMENTED: Article list');
};
```

X Add Routes

Next create the routes, and bind them to the controllers. Add `routes/app.routes.js`:

```
var express = require('express');
var router = express.Router();

var articlesController = require('../controllers/articles')
var aboutController = require('../controllers/about')

router.get('/', articlesController.article_list);

router.get('/articles/:articleid', articlesController.article_read);

router.post('/articles/add', articlesController.article_write);

router.get('/about', aboutController.about);

module.exports = router;
```

X Bind Routes

Finally, bind your routes to the app by adding them to `app.js`:

```
...
var routes = require('./app_server/routes/app.routes')
...
app.use('/', routes);
```

X NOTE

Express doesn't follow any specific architecture pattern, and this is just one example way to enable MVC. Using multiple routers could be used for decoupling.

## Creating Views

This article will not cover [Pug](https://pugjs.org) and [Bootstrap](https://getbootstrap.com) in depth - they are well documented anyway - but some pitfalls when used together.

X Responsive Layout

Beside using Bootstrap components, its layout system is key for building responsive web pages. To develop responsive sites, Bootstrap classifies the display width into:

* Extra small (XS) < 576px
* Small (SM) ≥ 576px
* Medium (MD) ≥ 768px
* Large (LG) ≥ 992px
* Extra large (XL) ≥ 1200px

X Bootstrap Containers

[Containers](https://getbootstrap.com/docs/4.5/layout/overview/#containers) are the most basic layout element, and are required when using the grid system. Containers have fixed width until a responsive breakpoint; only fluid containers span the entire viewport:

```
.container sets a max-width at each responsive breakpoint
.container-sm 100% wide until small breakpoint
.container-md 100% wide until medium breakpoint
.container-lg 100% wide until large breakpoint
.container-xl 100% wide until extra large breakpoint
.container-fluid is width: 100% at all breakpoints
```

X Bootstrap Grid System

Bootstrap layouts

 Bootstrap uses containers, rows, and columns to layout content. There are always 12 columns per row, regardless display width.

 With Bootstrap you can specify column grid classes: `col-sm`, `col-md`, `col-lg`, `col-xl`, wrapping the column at their breakpoint. A simple example:

 ```
.container.row
	.col-sm one
	.col-sm two
	.col-sm three
```

For a detailed description and examples check out the [Bootstrap grid system](https://getbootstrap.com/docs/4.5/layout/grid/).

X Pug Templates with Bootstrap

When using [Pug](https://pugjs.org) as template engine with Bootstrap you may have to understand the syntax.

Creating a navigation bar uses the `<nav>` element, followed by sub-components specified as HTML class attributes (`.navbar`, `.navbar-light`, `.bg-light`). With Pug however, you can simply use the dot notation to specify a class. Explicitly specifying an attribute is done within brackets, as `href`.

```
nav.navbar.navbar-light.bg-light
	a.navbar-brand(href="#") Navbar
```

X Extendable Layouts

With Pug templates you can make use of [template inheritance](https://pugjs.org/language/inheritance.html).

The `block` keyword defines a name which a sub-template may replace. The `extend` keyword in the sub-template import the parent template, and you can replace the `block`.

This comes in handy to create a general template style for multiple views.

This is an example of a template layout adding a [Bootstrap navbar](https://getbootstrap.com/docs/5.0/components/navbar/), and making it reusable for other templates defining the `block content`

```
doctype html
html
  head
    title= title
    link(rel='stylesheet', href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" )
    link(rel='stylesheet', href='/stylesheets/style.css')
  body  
    nav.navbar.navbar-light.bg-light
      a.navbar-brand(href="#") Navbar
    block content
    script(src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js")

```

X Setting up Views and Controllers

With routers and controllers set, you can create templates and bind them to the controller.

Create your templates at `views/`, like `views/about.pug`:

```
extends layout

block content
  h2 #{title}
```

Next you should bind them in the controllers. For the about page replace the code in the `controllers/about.js` to render the new template:

```
exports.about = function(req, res) {
    res.render('about', { title: 'About' });
};
```


The Express method `render` takes the name of the template and JavaScript data object as parameter, which you can bind in your template.

Watch your template rendered in the browser at [http://localhost:3000/about](http://localhost:3000/about).

## Move Data from View to Controller

X Updating Views & Controllers

A goal of MVC is to remove data from the view, and by doing so, making the view smarter.

Indeed, we already have moved the data to the controller, but let's have some more examples. Modify the controller `controllers/about.js`:

```
exports.about = function(req, res) {
    res.render('about', {
      title: 'About',
      content: { details: 'Lorem ipsum dolor sit amet' },
    });
};
```

And also update the view `views/about.pug`:

```
extends layout

block content
  h2 #{title}
  p #{content.details}
```

X Repeating data patterns

In more complex views you likely have to deal with repeating elements. In your controller just add a data array to inject into your view:

```
exports.about = function(req, res) {
    res.render('about', {
      title: 'About',
      content: { details: 'Lorem ipsum dolor sit amet' },
      list: [ 'one', 'two', 'three' ]
    });
};
```

The controller sends an array named `list` to the Pug template, where you can [iterate](https://pugjs.org/language/iteration.html) over it:

```
extends layout

block content
  h2 #{title}
  p #{content.details}


  ul
    each item in list
      li item
```

X Inline JavaScript code in Pug

Sometimes it may make sense to inline JavaScript into your template. To do so, Pug offers the option [inline code](https://pugjs.org/language/code.html).

```
extends layout

block content
  h2 #{title}
  p #{content.details}

  ul
    each item in list
      li item

  - for (var x = 0; x < 5; x++)
    i.fas.fa-star
```

X Mixins - reusable components

With [Pug mixin](https://pugjs.org/language/mixins.html) you can create reusable components, which can be used multiple times across your template, just like functions. This also makes changing them all at once easy.

Add a mixing to `views/article.pug` between `extend` and the `block content`, and use it wherever you want with a `+` prefixed:

```
extends layout

mixin link(href, name)
  a(href=href)= name

block content
  h2 #{title}
  p #{content.details}

  ul
    each item in list
      li item

  - for (var x = 0; x < 5; x++)
    i.fas.fa-star

  +link('http://127.0.0.1', 'localhost')
```


To get one step further, and make mixins reusable across multiple templates, create new Pug file - e.g. `views/mixins.pug` - where to you move the mixing:

```
mixin link(href, name)
  a(href=href)= name
```

Replace the mixin from `views/about.pug` by including the new mixins file:

```
extends layout

include mixins

block content
  h2 #{title}
  p #{content.details}


  ul
    each item in list
      li item

  - for (var x = 0; x < 5; x++)
    i.fas.fa-star

  +link('http://127.0.0.1', 'localhost')
```

## References

* [Pug](https://pugjs.org)
* [Bootstrap](https://getbootstrap.com)
* [Express](http://expressjs.com)
* [Mozilla - Routes and Controllers](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/routes)
* [Bootstrap Containers](https://getbootstrap.com/docs/4.5/layout/overview/#containers)
* [Bootstrap grid system](https://getbootstrap.com/docs/4.5/layout/grid/)
* [Pug Template Inheritance](https://pugjs.org/language/inheritance.html)
* [Pug iterate](https://pugjs.org/language/iteration.html)
* [Pug inline code](https://pugjs.org/language/code.html)
* [Pug mixin](https://pugjs.org/language/mixins.html)
