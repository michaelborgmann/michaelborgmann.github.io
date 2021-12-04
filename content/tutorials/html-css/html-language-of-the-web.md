---
title: "1. Html Language of the Web"
slug: html-language-of-the-web
date: 2021-06-18T00:32:37+01:00
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

Getting to know HTML - The Language of the Web

<!--more-->

*Almost originally from HF*

## The Internet

* Big picture
* What web servers do
* What web browser do
* What you write (HTML)
* What the browser creates

## Creating an HTML file

* Create a HTML document
* Save the document
* See in browser

## Tags

* ``<h1>`` - heading
* ``<h2>`` - subheading
* ``<p>`` - block of text that is a paragraph
* ``<html>`` - tells the browser the file HTML
* ``<head>`` - contains information about your web page
* ``<title>`` - title of web page, usually at the browsers top
* ``<body>`` - contains all content and structure of the web page

### Basic HTML Structure

```
<html>
  <head>
	  <title>YOUR TITLE HERE</title>
  </head>

  <body>
	  <h1>Headline</h1>
	  <h2>Sub-header</h2>
	  <p>Paragraph</p>
  </body>
</html>
```

## Tags dissected

``<h1>HEADLINE</h1>``

* Opening tag
* Content is enclosed by tags
* Closing tag; having a slash
* The whole thing is called element (tag, enclosing tag, content); element = opening tag + content + closing tag

## The ``<style>`` element

```
<html>
	<head>
		<style type="text/css">

		</style>
	</head>
	<body>
	</body>
</html>
```

* the ``<style>`` element is placed inside the ``<head>``
* has an optional attribute called type, which tells the browser which kind of style to use. For CSS specify "text/css"
* Attributes give additional information about an element

### Style Syntax

```
<style type="text/css">
	body {
		background-color: #2f3d12;
		margin-left: 20%;
		margin-right: 20%;
		border: 2px dotted black;
		padding: 10px 10px 10px 10px;
		font-family: sans-serif;
	}
</style>
```

## HTML vs. CSS

* HTML is about structure
* CSS is about styling

## Bullet Points

* HTML and CSS are the languages we use to create web pages
* Web servers store and serve web pages, which are created from HTML and CSS. Browsers retrieve pages and render their content based on the HTML and CSS.
* HTML is an abbreviation for Hyper Text Markup Language and is used to structure your web page
* CSS is an abbreviation for Cascading Style Sheets, and is used to control the presentation of your HTML.
* Using HTML, we mark up content with tags to provide structure. We call matching tags, and their enclosed content, elements.
* An element is composed of three parts: an opening tag, content, and closing tag. There are a few elements, like ``<img>``, that are an exception to this rule.
* Opening tags can have attributes. We've seen one already: type.
* Closing tags have a "/" after the left angle bracket, in front of the tag name, to distinguish them as closing tags.
* Your pages should always have an ``<html>`` element along with a ``<head>`` element and a ``<body>`` element.
* Information about the web page goes into the ``<head>`` element.
* What you put into the ``<body>`` element is what you see in the browser.
* Most whitespace (tabs, returns, spaces) is ignored by the browser, but you can use it to make your HTML more readable (to you).
* You can add CSS to an HTML web page by putting the CSS rules inside the ``<style>`` element. The ``<style>`` element should always be inside the ``<head>`` element.
* You specify the style characteristics of the elements in your HTML using CSS.
