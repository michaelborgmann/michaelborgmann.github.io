---
title: "2. Setting Up The First Project"
slug: setting-up-the-first-project
date: 2021-06-18T10:59:27+01:00
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

Setting up a project with Atom

<!--more-->

1. Create a project folder
2. Create an index.html in root
3. Create a stylesheets folder
4. Create a styles.css file within stylesheets

## Initial HTML

Autocompleted basic HTML block by Atom:

	<!DOCTYPE html>
	<html lang="en" dir="ltr">
	  <head>
	    <meta charset="utf-8">
	    <title></title>
	  </head>
	  <body>

	  </body>
	</html>

### TITLE

	<title> </title>

### HEADER

	<header> </header>

### MAIN

	<main> </main>

### HEADLINE

	<h1> </h1>

### DIV

A `<div>` is a generic container for content, usually to apply styling to the enclosed content.

	<div>
		...
	</div>

## Linking a stylesheet

	 <head>
		 ...
		 <link rel="stylesheet" href="stylesheets/style.css">
	 </head>

## Content

### Unordered Lists

	<ul>
		<li>
			<span> </span>
		</li>
		...
	</ul>

### SPAN

	<span> </span>

`<span>` tags have no special meaning, and are generic containers for other content.

## Adding Images

	<a href="#">
		<img src="img/image.jpg" alt="description">
	</a>

### Anchor tags

`<a>` is a clickable anchor tag, taking users to another page (links).

The `href` attribute indicates the resource, usually a web address. The value `#` indicates a dummy value, linking nowhere.

## Viewing the Web Page in the Browser

	$ browser-sync start --server --browser "Google Chrome" --files "stylesheets/*.css, *.html"

## Chrome Developer Tools

- DOM tree view
