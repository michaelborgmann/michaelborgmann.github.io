---
title: "2. Meeting Hypertext"
slug: meeting-hypertext
date: 2021-06-18T09:41:49+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
sidebar:
- "[1. HTML - Language of the Web](/tutorials/html-css/html-language-of-the-web/)"
- "[2. Meeting Hypertext](/tutorials/html-css/meeting-hypertext/)"
- "[3. Web Page Construction](/tutorials/html-css/web-page-construction/)"
- "[4. Getting Online](/tutorials/html-css/getting-online/)"
- "[5. Adding Media](/tutorials/html-css/adding-media/)"
- "[6. HTML Standards](/tutorials/html-css/html-standards/)"
- "[7. Adding CSS Styles](/tutorials/html-css/adding-css-styles/)"
- "[8. Styling Fonts Colors](/tutorials/html-css/styling-fonts-colors/)"
- "[9. The Box Model](/tutorials/html-css/the-box-model/)"
- "[10. DIVs and SPANs](/tutorials/html-css/divs-and-spans/)"
- "[11. Layout and Positioning - Arranging Elements](/tutorials/html-css/layout-and-positioning-arranging-elements/)"
- "[12. HTML Markup - Modern HTML](/tutorials/html-css/html-markup-modern-html/)"
---

Going further wither hypertext - Meeting the "HT" in HTML

<!--more-->

*Almost originally from HF*

## Tags

* ``<img src="filename.jpeg">``
``<a href="linkname.html">TEXT</a>``

### ``<a>``

``<a href="linkname.html">TEXT</a>``

* the ``<a>`` element is used to crate a link to another page
* The content of the ``<a>`` element is the link text, and appears with an underline indicating to be clickable.
* The href attribute specifies the destination of the link.

Use the ``<a>`` element to create a hypertext link to another web page. The content of the ``<a>`` element becomes clickable in the web page. The href attribute tells the browser the destination of the link.

## Understanding Attributes


Attributes provide a way to specify additional information about an element.

## Folder structure

* Organise files and folders
* Linking into paths

## Bullet Points

* When you want to link from one page to another, use the ``<a>`` element.
* The href attribute of the ``<a>`` element specifies the destination of the link.
* The content of the ``<a>`` element is the label for the link. The label is what you seen on the web page. By default it's underlined to indicate you can click on it.
* You can use words or an image as the label for a link.
* When you click on a link, the browser loads the web page that's specified in the href attribute.
* You can link to files in the same folder, of files in other folders.
* A relative path is a link that points to other files on your website relative to the web page you're linking from. Just like on a map, the destination is relative to the starting point.
* Use "..." to link to a file that's one folder above the file you're linking from.
* ".."means "parent folder."
* Remember to separate the parts of your path with the "/" character.
* When your path to an image is incorrect, you'll see a broken image on your web page.
* Don't use spaces in the names you choose for files and folders for your website.
* It's a good idea to organise your website files early on in the process of building your site, so you don't have to change bunch of paths later when the website grows.
* There are many ways to organise a website; how you do it is up to you.
