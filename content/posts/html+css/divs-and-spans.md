---
title: "Divs and Spans (10/13)"
date: 2021-06-18T10:29:01+01:00
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

divs and spans - Advanced Web Construction

<!--more-->

* Identify logical sections (group of elements that are all related on the page).
* Use <div>s to mark sections
* Labeling <div>s, e.g. with an id attribute to provide a unique labe for the <div>
* Adding some style
* Expose even more structure. This will help understanding and maintaining the page
* Add structure on structure (nesting structures)

<div>s are container to put elements to.

Use, don't abuse, <div>s in your page. Add more structure where it helps you separate a page into logical sections for clarity and styling. Adding <div>s just for the sake of creating a lot of structure in your pages complicates them with no real benefit.

## width property

``width: 200px;``

* The width property lets you specify the width of the element's content area.
* The width property specifies the width for the content area only. To figure out the width of the entire box, add the content + left & right margin & padding + 2x border.
* The default width for a block element is "auto", which means that it will be expand to fill whatever space is available.
* You can specify width in pixels or percentage.
* The height of an element is left at the default, which is auto, and the browser expands the content area vertically so all of the content is visible. You can set a height, but risk having the bottom of your content overflow into other elements

## Select descendants

Select elements that descend from certain elements

```
div h2 {
	color: black;
}

#idname h2 {
	color: black;
}
```

## Margin & Padding shortcut

Instead of (and also for margin):

```
padding-top: 0px;
padding-right: 20px;
padding-bottom: 30px;
padding-left: 19px;
```

just write:

```
margin: 0px 20px 30px 10px;
padding: 0px 20px 30px 10px;
```

If every side has the same value:

```
padding: 20px;
```

For borders:

```
border: solid thin #007e8e;
```

And for backgrounds:

```
background: white url(image/filename.jpg) repeat-x;
```

For fonts:

```
font: font-style font-variant font-weight font-size/line-height font-family

font: small/1.6em Verdana, Helvetical, Arial, sans-serif;
```

## Adding ``<span>``'s

The ``<span>`` element provides a way to logically separate inline content in the same way that ``<div>`` create logical separation for block-level content.

1. Adding the ``<span>``

```
<ul>
	<li>
		<span class="cd">Buddha Bar</span>, <span class="artist">Claude Challe</span>
		</li>
</ul>
```

2. Apply styling

```
.cd {
	font-style: italic;
}

.artist {
	font-weight: bold;
}
```

If you really want to change the style (not just ``<em>`` or ``<strong>``), then use ``<span>``.

## Multiple personalities of ``<a>``

The style of an ``<a>`` element changes depending on its *state*:

* unvisited: ``a:link { }``
* visited: ``a:visited { }``
* hover: ``a:hover { }``
* focus:
* active:

## Pseudo-class

* Pseudo means means something looks real, but isn't.
* A CSS class is grouping of elements, to style them together. Put together it acts like a class, but isn't a real class.
* There are no ``:visited``, ``:link`` or ``:hover`` in HTML, yet allow styling just like a class.
* The browser add in the right pseudo-class
* There are also other pseudo-class:
	** :hover on other types
	** :first-child is assigned to the first child of an element
	** :last-child

```
#elixiers a:link {
	color: #007e7e;
}

#elixiers a:visited {
	color: #333;
}

#elixiers a:hover {
	background: #0d5353;
	color: #f88396;
}
```

## The Cascade

The cascade is the way the browser decided which style is going to be used.

1. Gather all stylesheets together
2. Find all declarations that match
3. Take all matches, and sort them in the order of: author, reader, browser.
4. Sort all declarations by how specific they are
5. Sort any conflicting rules in the order they appear in their individual stylesheets.

## Calculate the specificity

1. Start with a set of three number: 0 0 0
2. Tally up various things from the selector:
	* Does the selector have any ids? One point each
	* Does the selector have any classes or pseudo-classes? One point each
	* Does the selector have any element names? One point each

Example: The selector h1 has on element in it: 0 0 1
The selector h1.blue has one element and one class: 0 1 1

After tallying up ids, classes and elements, the bigger the specifity number, the more specific the rule. As h1.blue is 011, it's more specific than h1 with 001.

## Bullet Points

* ``<div>`` elements are used to group elements together into logical sections.
* Creating logical sections can help you identify the main content areas, header, and footer of your page
* You can use ``<div>`` elements to group elements together that need a common style.
* Use nested ``<div>`` elements to add further structure to your files for clarity or styling. But don't add structure unless you really need it.
* Once you have grouped together sections of content with ``<div>`` elements, you can style the ``<div>`` just like you would any other block element. For example, you can add a border around a group of elements using the border property on the ``<div>`` they are nested in.
* The width property sets the width of the content area of an element.
* The total width of an element is the width of the content area, plus the width of any padding, border, and margins you add.
* Once you set the width of an element, it no longer expands to fit the entire width of the browser window.
* Text-align is a property for block elements that aligns all incline content in the block element, to the center, left or right. It is inherited by any nested block elements
* You can use descendant selectors to select elements nested within other elements. For instance, the descendant selector ``div h2 { ...}`` selects all ``<h2>``s nested in ``<div>`` elements (including children, grandchildren, etc).
* You can use shortcuts for related properties. For instance, padding-top, padding-right, padding-bottom, and padding-left are all related to padding, and can be specified with on shortcut rule, padding.
* Padding, margin, border, background, and font properties can all be specified with shortcuts.
* The ``<span>``inline element is similar to the ``<div>`` element: It is used to group together related inline elements and text.
* Just like with <div>, you can add ``<span>`` elements to classes (or give ``<span>`` elements unique ids) to style them.
* The ``<a>`` element is an example of an element with different states. The main ``<a>`` element states are unvisited, visited, and hover.
* You can style each of these states separately with pseudo-classes. The pseudo-classes used most often with the ``<a>`` element are :link, for unvisited links; :visited, for visited links, and : hover, for the hover state.
* Psudeo-classes can be used with other lements too, not just ``<a>``.
* Additional pseudo-classes are the :hover, :active, :focus, :first-child, and :last-child pseudo-classes, among others.
