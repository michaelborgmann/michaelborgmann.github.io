---
title: "HTML Standards (6/13)"
date: 2021-06-18T10:09:07+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
series: HTML & CSS
categories:
- Web
tags:
- HTML
- CSS
---

Standards and all that jazz - Getting Serious with HTML

<!--more-->

*Almost originally from HF*

## HTML History

* HTML 1.0-2.0 (1989, 1991)
* HTML 3 (1995)
* HTML 4 (1998)
* HTML 4.01 (1999)
* XHTML 1.0 (2001)
* HTML 5 (2009-2012)

## The HTML5 doctype

``<!doctype html>``

## HTML is a living standard

In future, the HTML specification turned into a living standard that will document the technology as it evolves. No more version numbers. You don't have to call it HTML5 because it's just HTML from here on out.

The implemented feature will be usable in the future, while new features will be added, and have implemented to the browser.

## Adding ``<meta>`` tag to specify the character encoding.

Character encodings give us a way to represent all the letters, numbers and other symbols in our language on the computer. The world has now standardized on Unicode character encoding. With Unicode, we can represent all languages with one type of encoding.

But as there are still other encodings out ther, we still need to tell the browser we-re using Unicode (or another).

To specif Unicode for your web pages, you'll need a ``<meta>`` tag in your HTML:

```
<meta charset="utf-8">
```

* meta means we're going to tell the browser something about the page
* The charset attribute is where we specify the character encoding
* utf-8 is an encoding in the Unicode family of encodings, utf-8 is the version we use for web pages.
* the value of the charset attribute is the type of character encoding we're using

## Webville Guide to HTML

* Always begin with the ``<doctype>``
* the ``<html>`` element: doesn't leave home without it.
* remember to use both your ``<head>`` and your ``<body>`` for better HTML.
* feed your ``<head>`` the right character encoding.
* what's a ``<head>`` without a ``<title>``
* Be careful about nesting certain elements.
* Check your attributes!

## Bullet Points

* HTML5 is the current HTML standard.
* The document type definition (doctype) is used to tell the browser the version of HTML you're using
* The HTML standard is now a "living standard", which means that the standard will change to incorporate new features and updates.
* The ``<meta>`` tag in the ``<head>`` element tells the browser additional information about a web page, such as the content type and character encoding.
* The charset attribute of the ``<meta>`` tag tells the browser the character encoding that is used for web page
* Most web pages use the utf-8 encoding for HTML files, and for the ``<meta>`` tag charset attribute.
* The alt attribute is required for the ``<img>`` element
* The W3C validator is a free online service that checks pages for compliance with standards.
* Use the validator to ensure that your HTML is well formed and that your elements and attributes meet the standard.
* By adhering to the standard, your pages will display more quickly and with fewer display differences between browsers, and your CSS will work better.
