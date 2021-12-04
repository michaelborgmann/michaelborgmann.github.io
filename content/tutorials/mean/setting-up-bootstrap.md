---
title: "4.1 Setting Up Bootstrap"
slug: setting-up-bootstrap
date: 2021-06-18T10:40:39+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
sidebar:
- "[1. Full Stack Development](/tutorials/mean/full-stack-development/)"
- "[2. MEAN Stack Architecture](/tutorials/mean/mean-stack-architecture/)"
- "[3. Building Node.js Apps](/tutorials/mean/building-nodejs-apps/)"
- "[4. MVC Architecture](/tutorials/mean/mvc-architecture/)"
- "[4.1 Setting up Bootstrap](/tutorials/mean/setting-up-bootstrap/)"
- "[4.2. Deploy on Heroku](/tutorials/mean/deploy-on-heroku/)"
- "[5. Static Pages](/tutorials/mean/static-pages/)"
- "[6. Building the Data Model with MongoDB and Mongoose](/tutorials/mean/building-the-data-model-with-mongodb-and-mongoose/)"
---

*Create and Setting up a MEAN project II*

This article will cover useful additions to the MEAN stack - like Bootstrap, etc.

<!--more-->

## Setup Bootstrap

[Bootstrap](https://getbootstrap.com) is framework to rapidly build responsive, mobile-first websites.

To add Bootstrap to your Express app you have to:

* Reference the Bootstrap CSS files
* Reference the Bootstrap JavaScript file
* Reference jQuery and Popper.js
* Add viewport metadata to scale for mobile devices

In [Express](http://expressjs.com) with [Pug](https://pugjs.org) as template engine enabled add those to the `layout.pug` file. References to CSS files should be added to the head, while references to JavaScript files should be at the body's bottom.

However, there are different ways to [install Bootstrap](https://getbootstrap.com/docs/4.5/getting-started/download), but here we'll cover installation by CDN or npm.

### Bootstrap by CDN

You can easily add Bootstrap by using the open source CDN [jsDelivr](https://www.jsdelivr.com). Just [copy & paste](https://getbootstrap.com/docs/4.5/getting-started/download/#jsdelivr) the code, and modify it according to the template engine (here Pug):

```
doctype html
html
  head
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title= title
    link(rel='stylesheet', href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css" integrity="sha384-TX8t27EcRE3e/ihU7zmQxVncDAy5uIKz4rEkgIXeMed4M0jlfIDPvg6uqKI2xXr2" crossorigin="anonymous")
    link(rel='stylesheet', href='/stylesheets/style.css')
  body
    block content
    script(src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ho+j7jyWK8fNQe+A12Hb8AhRq26LrZ/JpcUGGOn+Y7RsweNrtN/tE3MoK7ZeZDyx" crossorigin="anonymous")
```

This Bootstrap script already bundles Bootstrap + [Popper](https://popper.js.org) + [jQuery](https://jquery.com).

### Bootstrap by npm

Optionally, you can add Bootstrap by npm to your Node app:

`$ npm install bootstrap`

## Font Awesome

[Font Awesome](https://fontawesome.com) is an open-source icon set. You can download and install it locally to your project, by npm or another package manager, but also by CDN after registration and you'll get receive an email containing a script reference to be added to your template head:

```
head
	script(src="https://kit.fontawesome.com/e6f276d84a.js" crossorigin="anonymous")
```

To find an icon, head to the [gallery](https://fontawesome.com/icons?d=gallery). Font Awesome is designed to work with the `<i>` or `<span>` tag. The icon name is prefixed with **fa-** (e.g. **fa-apple**). At last, you have to specify a style:

* `fas` = solid
* `far` = regular (pro)
* `fal` = light (pro)
* `fad` = duotone (pro)
* `fab` = brands

To add an icon to your Pug template just add it to your body (here the Apple logo): `i.fab.fa-apple`

## Resources

* [Twitter Bootstrap](https://getbootstrap.com)
* [Express](http://expressjs.com)
* [Pug](https://pugjs.org)
* [jsDelivr](https://www.jsdelivr.com)
* [Popper](https://popper.js.org)
* [jQuery](https://jquery.com)
* [Bootstrap installation](https://getbootstrap.com/docs/4.5/getting-started/download)
* [Font Awesome](https://fontawesome.com)
* [Font Awesome Gallery](https://fontawesome.com/icons?d=gallery)
