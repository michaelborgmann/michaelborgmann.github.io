---
title: "Web Page Construction (3/13)"
date: 2021-06-18T09:44:25+01:00
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

Building blocks - Web Page Construction

<!--more-->

*Almost originally from HF*

## Tags

* ``<q>`` - inline quote
* ``<blockquote>`` - quote used on their own block
* ``<br>`` - linebreak for inline elements
* ``<li>`` - list item
* ``<ol>`` - ordered list
* ``<ul>`` - unordered list
* ``<em>`` - emphasise text
* ``<time>`` - content is a date or time or both
* ``<code>`` - source code
* ``<strong>`` - extra strong emphasise
* ``<pre>`` - show text exactly as you typed

## Blocks vs inline

Blocks are always displayed as if they have a linebreak before and after them, while inline elements appear in line within the flow of the text in your page.

Block elements are often used as the major building blocks of a web page, while inline elements usually mark up small pieces of content.

## Void elements

Elements that don't have any content by design are called void elements. When you need to use a void element, like ``<br>`` or ``<img>``, you only use an opening tag. This a convenient shorthand that reduces the amount of markup in your HTML.

## Character entities

* Character entity is an abbreviation for special characters
* &gt; is >
* &lt; is <
* &amp; is & (ampersand)

Full list at:

* http://www.w3schools.com/tags/ref_entities.asp
* http://www.unicode.org/charts/

## Bullet Points

* Plan the structure of your web pages before you start typing in the content. Start with a sketch, then create an outline, and finally write the HTML.
* Plan your page starting with the large, block elements, and then refine with inline elements.
* Remember, whenever possible, use elements to tell the browser what your content means.
* Always use the element that most closely matches the meaning of your content. For example, never use a paragraph when you need a list.
* ``<p>``, ``<blockquote>``, ``<ol>``, ``<ul>``, and ``<li>`` are all block elements. They stand on their own and are displayed (by default) with a linebreak above and below the content within them.
* ``<q>`` and ``<em>`` are inline elements. The content in these elements flows in line with the rest of the content in the containing element.
* Use the ``<br>`` element when you need to insert your own linebreaks.
* ``<br>`` is a "void element".
* A void element consists of only one tag.
* An "empty"element has no content. But it does have both opening and closing tags.
* A nested element is an element contained completely within another element. If your elements are nested properly, all your tags will match correctly.
* You make an HTML list using two elements in combination: use ``<ol>`` with ``<li>`` for an ordered list; use ``<ul>`` with ``<li>`` for an unordered list.
* When the browser displays an ordered list, it creates the numbers for the list so you don't have to.
* You can build nested lists within lists by putting ``<ol>`` or ``<ul>`` elements inside your ``<li>`` elements.
* Use character entities for special characters in your HTML content.
