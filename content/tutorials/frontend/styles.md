---
title: "3. Styles (3/10)"
slug: styles
date: 2021-06-18T10:59:36+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
sidebar:
- "[1. Setting Up the Development Environment](/tutorials/frontend/setting-up-the-development-environment/)"
- "[2. Setting Up the First Project](/tutorials/frontend/setting-up-the-first-project/)"
- "[3. Styles](/tutorials/frontend/styles/)"
- "[4. Responsive Layouts with Flexbox](/tutorials/frontend/responsive-layouts-with-flexbox/)"
- "[5. Adaptive Layouts with Media Queries](/tutorials/frontend/adaptive-layouts-with-media-queries/)"
---

Styles

- Top down styling: From the overall layout down to the smallest details
- Atomic styling: From smallest details to overall layout. This usually produces more cleaner, more reusable code.

<!--more-->

## Creating a Styling Baseline

### normalize.css

- [get normalize](cdnjs.com/libraries/normalize)
	- get the smaller `.min.css`
	- CDN = Content Delivery Network

Link stylesheets

	<head>
		...
		<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
	</head>

Be sure to add the link tag for normalize before other custom links to stylesheets.

## Preparing HTML for Styling

### CLASS attributes

`class` attributes are a way to identify a group of HTML elements, usually for styling.

	<span class="identifier">

### ID attributes

*ID selectors* have the highest degree of specificity:

	<li class="class-item" id="identifier">

Style an ID in a selector:

	#identifier {
		...
	}

NOTE: ID attributes might be unique, but their associated styles cannot be reused, making them a maintenance "worst practice".

## Anatomy of a Style

A style consists of two main parts: ***selectors*** and ***declerations***. Styles can have one or more selectors

	selector(s) {
		declarator/property: value;
	}


### Comments

	/* this is a comment */

### Class Selector Styling Rule

	.class-name {
		...
	}

### Element Selector Styling Rule

	body {
		...
	}


## Relationship selectors

Relationship selector syntax includes two selectors joined by a ***combinator***, which is read from right to left.

### Descendent Selector

Target element of a specified type that is the descendent of another specified element.

Select any `span` element that is the descendent of the `body` element (without combinator):

	body span {
		...
	}

You can also use a class selector (or attribute selector, or any type of selector) within a relationship selector:

	body .thumbnail-title {
		...
	}

### Child Selector

Target elements of a specified type that are the immediate children of another specified element, using the combinator `>`.

Select any `span` that is the immediate child of a `li` element:

	li > span {
		...
	}

### Sibling Selector

Uses the combinator `~`, and targets elements with the same parent.

Target any `ul` that is preceded by a `header` with the same parent element:

	header ~ ul {
		...
	}

### Adjacent Sibling Selector

Target elements that are immediately preceded by a sibling of the specified type - using combinator `+`.

Select all `li` elements immediately preceeded by a sibling `li`:

	li + li {
		...
	}

NOTE: This selector can be used to style all elements, except the first

## Styles

### width & height

	width: 100%;
	height: 100%;

When setting `height: 100%` for the `<html>` and `<body>`, the root and child element of the DOM tree, this allows the content to fill the browser or device window.

	html, body {
		height: 100%;
	}

TRICK: Remove variations in size (with flexbox):

	.style {
		/* width: 120px; */
		min-width: 120px;
		max-width: 120px;
	}

### margin & padding

Every drawn element uses a scheme called the ***standard box model*** (content > padding > border > margin).

	marging: 0;
	padding: 4px 10px;

### display

The `display` property tells how an element should flow in the layout.

When applying `display` styles, think of block elements *flow* from top to bottom and inline elements flow from left to right.

Occupy entire width of containing element:

	display: block;

Make element's width fit its content:

	display: inline;

NOTE: Images are `display: inline` by default, and include some whitespace below the baseline. Use `default: block` to remove the whitespace.

Draw as with `display: block`, but without line breaks:

	display: inline-block;

### background & color

	background: rgb(96, 125, 139);
	color: rgb(202, 238, 255);

### border

	border: 1px solid rgb(100%, 100%, 100%);
	border: 1px solid rgba(100%, 100%, 100%, 0.8);

NOTE: Some browsers don't support `rgba`, so providing both declarations is a fallback technique.

### fonts

Center text inside element:

	text-align: center;

Format text to uppercase:

	text-transform: uppercase;

Set font size:

	font-size: 18px;

Select font family (declared by `font-face`):

	font-family: lakeshore;

Add shadow to text (x, y, blur radius in px):

	text-shadow: rgba( 0, 0, 0, 0.9) 1px 2px 9px;

### @font-face syntax

The `@font-face` syntax gives a custom name to a family of fonts to use in the rest of your styles.

A `@font-face` block consists of:
1. `font-family` property to identify the custom font name.
2. Several `src` declarations specifying different font files (order is important).
3. Declarations that modify the font's presentation, such as `font-weight` and `font-style`.

Add `@font-face` declaration to the top of the CSS file:

	@font-face {
		font-family: 'lakeshore';
		src: url('fonts/LAKESHOR-webfont.eot');
		src: url('fonts/LAKESHOR-webfont.eot?#iefix') format('embedded-opentype'),
			url('fonts/LAKESHOR-webfont.woff') format('woff'), url('fonts/LAKESHOR-webfont.ttf') format('truetype'), url('fonts/LAKESHOR-webfont.svg#lakeshore') format('svg');
		font-weight: normal;
		font-style: normal; }
	}

NOTE: Place the `fonts` folder into your project inside the `stylesheets` folder.

### anchor tag styling

Remove underline:

	a {
		text-decoration: none;
	}

### lists

Get rid of bullet points:

	list-style: none;

### scrolling list

Prevent elements from wrapping:

	white-space: nowrap;

Add scrollbar along horizontal space (otherwise you'd have to scroll the entire webpage):

	overflow-x: auto:

## Style Inheritance

In the DOM, styles will be inherited by their descendents.

Chromes DevTools give you a prompt to try out on the fly for the `element.style`.
