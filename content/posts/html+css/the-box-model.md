---
title: "The Box Model (9/13)"
date: 2021-06-18T10:26:44+01:00
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

The box model - Getting Intimate with Elements

<!--more-->

*Almost originally from HF*

## Tags

* Space between each line: ``line-height: 1.6em``

## Everything is a box

* From the perspective of CSS, every element is a box
* Every box is made up of a content area along with optional padding, border, and margins.
* The content area holds the content (text or an image for instance)
* The content area is surrounded by optional transparent padding.
* An optional border can be placed around the padding.
* And finally, an optional transparent marin surrounds everything

## A closer look at the box model

* A content are is the place where content is put inside a box, just enough to contain, without whitespace between content and the edge of this box.
* Padding is the layer area around the content, to create visual whitespace between content and the border of the box. Padding is transparent and has no color or decoration.
* The border surrounds the padding, and can take the form of a line, providing visual separation between content and other elements. Borders can have various widths, colors, and styles.
* Margin is an optional surrounding layer around the border, and gives space between elements. Like padding, margins are transparent and have not color or decoration.

## What can you do to boxes

It may look simple, but you can combine the box model in countless ways to determine the layout of tan element with its internal spacing and around.

## Tags

* ``border-color: black;``
* ``border-width: 1px;``
* ``border-style: solid;``
* ``background-color: #a7cece;``
* ``padding: 25px;``
* ``margin: 30px;``

## Background Image

``background-image: url(images/background.gif);``

* Set background-image property is set to a URL
* Notice that no quotes are required around the URL

``background-repeat: no-repeat;``

* By default, a background image is tiled, or repeated over and over to fill the background space. The background-repeat property controls how this tiling behaves.
* ``repeat`` - repeats horizontally and vertically (default)
* ``no-repeat`` - display once, don't repeat
* ``repeat-x`` - repeat horizontally
* ``repeat-y`` - repeat vertically
* ``inherit`` - do what the parent element does

``background-position: top left;``

* The background-position property sets the position of the image anc can be specified in pixels, or as a percentage, or by using keywords like top, left, right, bottom, and center.

## A two-minute guide to borders

The ``border-style`` property controls the visual style of the border. There are eight border styles available, from a solid line to dotted lines to ridges and grooves.

``border-style: groove;``

* ``solid`` - just a solid border
* ``double`` - uses two lines
* ``groove`` - looks like a groove in the page
* ``outset`` - looks like an outet that rises from the page
* ``dotted`` - series of dots
* ``dashes`` - series of dashes
* ``inset`` - like an inset, sinking into the page
* ``ridge`` - looks like a raised ridge

The ``border-width`` property controls the width of the border; with keywords or pixels;

* ``border-width: thin;`` (thin, medium, thick
* ``border-width: 5px;``

The ``border-color`` property sets the color of the border; using named, rgb, or hex

* ``border-color: red;``
* ``border-color: rgb(100%, 0%, 0%);``
* ``border-color: #ff0000;``

Specifying Border Sides; just as with margins and padding, you can specify border style, width, or color on any side (top, right, bottom, or left):

* ``border-top-color: black;``
* ``border-top-style: dashed;``
* ``border-top-width: thick;``

Specifying border corners: You can create rounded corners for all four corners, or just one corner, or any combination:

* ``border-radius: 15px;``
* ``border-top-left-radius: 3em;``
* ``border-top-right-radius: 3em;``
* ``border-bottom-right-radius: 0px;``
* ``border-bottom-left-radius: 0px;``

## The id attribute

Id are for unique elements, while classes are meant to be reused.

## Multiple stylesheets

* In your HTML you can specify more than one stylesheet.
* Order matters. A stylesheet can override the styles in the stylesheets linked above it

Multiple style files may to fit your page's style to type of device (desktop, laptops, tables, smartphone, or even printed).

That's where the ``media`` attribute can be added to the ``<link>`` element, that lets you use only the style files that are appropriate for your device:

``<link href="styles-mobile.css" rel="stylesheet" media="screen and (max-device-width: 480px)">``

* The media attribute allows you to specify the type of device the stylesheet is for
* You specify the type of device by creating a "media query", which is matched with the device.
* Here our query specifies anything with a screen (as opposed to, say, a printer, or 3d glasses, or a braille reader)...
* ... and any device that has a width of at most 480 pixels

Likewise, we could create a query that matches the device if it is a printer:

``<link href=styles-print.css rel="stylesheet" media="print">``

There are a variety of properties to use in queries:

* ``min-device-width``
* ``max-device-width``
* ``orientation`` (landscape or portrait)

## Add media queries right int your CSS

There's another way to target your CSS to devices with specific properties. Rather than using media queries in link tags, you can also use them right in your CSS:

```
@media screen and (min-device-width: 481px) {
	#someId {
		margin-right: 250px;
	}
}

@media screen and (max-device-width: 480px) {
	#someId {
		margin-right: 30px;
	}
}

@media print {
	body {
		font-family: Times, "Times New Roman", serif;
	}
}
```

NOTE: Media queries are an area of active development by the standards group, so keep your eyes on evolving best practices for targeting devices.

## Bullet Points

* CSS uses a box model to control how elements are displayed
* Boxes consist of the content area and optional padding, border, and margin.
* The content area contains the content of the element.
* The padding is used to create visual space around the content area
* The border surrounds the padding and content and provides a way to visually separate the content.
* The margin surrounds the border, padding, and content, and allows space to be added between the element and other elements.
* Padding, border, and margin are all optional.
* An element's background will show under the content and the padding, but not under the margin.
* Padding and margin size can be set in pixels or percentages.
* Border width can be set in pixels or by using the keywords thin, medium, and thick.
* There are eight different styles for borders, including solid, dashed, dotted and ridge.
* For margins, padding, or the border, CSS provides properties for setting all the sides (top, right, bottom, left) at once, or it allows them to be set independently.
* Use the border-radius property to create rounded corners on an element with a border.
* Use the line-height property to add space between lines of text.
* You can place an image in the background of an element with background-image property.
* Use the background-position and background-repeat properties to set the position and tiling behaviour of the background image
* Use the class attribute for elements that you want to style together, as a group.
* Use the id attribute to give an element a unique name. You can also use the id attribute to provide a unique style for an element.
* There should only be one element in a page with a given id.
* You can select elements by their id using the id selector, for example #myfavoriteid.
* An element can have only one id, but it can belong to many classes.
* You can use more than one stylesheet in your HTML
* If two stylesheets have conflicting property definitions, the stylesheet that is last in the HTML file receive preference.
* You can target devices by using media queries in your ``<link>`` element or the @media rule in your CSS.
