---
title: "Getting Online (4/13)"
date: 2021-06-18T09:55:39+01:00
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

Getting connected - A trip to Webville

<!--more-->

*Almost originally from HF*

## Finding a hosting company

## Domain name

## Getting files to the server

## URL

A Uniform Resource Locator (URL) is a global address that can be used to locate anything on the Web, including HTML pages, audio, video, and many other forms of web content.

In addition to specifying the location of the resource, a URL also names the protocol that you can use to retrieve that resource.

## HTTP

* HyperText Transfer Protocol

## Absolute Path

## Default pages

* index.html

## Adding Title to Links

```
<a href="http://domainname.com" title="Description of Link">some text here</a>
```

## Linking into Page

* use an id attribute to create a destination for ``<a>`` (e.g. ``<h2 id="destination">some text</h2>``
* Link to elements with ids: ``<a href="index.html#destination">link to destination</a>``

## Tags

* ``<b>`` - bold text
* ``<i>`` - italic text

## Linking to a new windows

Opening a new window using target

```
<a target="_blank" href="http://domainname.com" title="description">link text</a>
```

The target attribute tells the browser the "target window" for the page. I used "_blank" the browser will always open a new display.

Some browsers will open new tabs.

## Bullet Points

* Typically the best way to get on the Web is to find a hosting company to host your web pages.
* A domain name is a unique name, like amazon.com or starbuzzcoffeee.com, that is used to identify a site.
* A hosting company can create one or more web servers in your domain. Servers are often named "www".
* The File Transfer Protocol (FTP) is a common means of transferring your web pages and content to a server.
* FTP applications, like Fetch for Mac or WS_FTP for Windows, can make using FTP easier by providing a graphical user interface.
* A URL is a Uniform Resource Locator, or web address, that can be used to identify any resource on the Web.
* A typical URL consists of a protocol, a website name, and an absolute path to the resource.
* HTTP is a request and response protocol used to transfer web pages between a web server and your browser.
* The file protocol is used by the browser to read pages from your computer.
* An absolute path is the path from the root folder to a file.
* "index.html" and "default.html" are examples of default pages. If you specify a directory without a filename, the web server will look for a default page to return to the browser.
* You can use relative paths or URLs in your ``<a>`` element's href attribute to link to other web pages. For other pages in your site, it's best to use relative paths, and use URLs for external links.
* Use the id attribute to create a destination in a page. Use # followed by a destination id to link to that location in a page.
* To help accessibility, use the title attribute to provide a description of the link in ``<a>`` elements.
* Use the target attribute to open a link another browser window. Don't forget that the target attribute can be problematic for users on a variety of devices and alternative browsers.
