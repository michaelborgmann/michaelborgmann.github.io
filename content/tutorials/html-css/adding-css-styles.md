---
title: "7. Adding Css Styles"
slug: adding-css-styles
date: 2021-06-18T10:12:15+01:00
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

Getting started with CSS - Adding a Little Style

<!--more-->

*Almost originally from HF*

Using CSS with HTML

```
p {
	background-color: red;
}
```

* first, select the element you want to style
* specify the property you want to style
* separate property and value with a colon
* add a value to the property
* add a semicolon at the end
* place all styes for element in between {} braces
* the whole thing is called RULE

## Styles

* ``background-color: red;`` - style the elements background color
* ``border: 1px solid gray; `` - style the elements border being 1 pixel thick, solid and gray


## Getting CSS into HTML

```
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<title>sites title</title>
		<style>

		</style>
	</head>
	<body>
	</body>
</html>
```

Add style directly to your HTML, adding the style tag in the head element. Add CSS rules into the style element.

## Style heading

```
	h1 {
		font-family: sans-serif;
		color: gray;
	}
```

* Change elements font-family to sans-serif and the font color to gray.

Combine style multiple elements

```
h1, h2 {

}
```

### But a line under text

```
h1, h2 {
	border-bottom: 1px solid black;
}
```

## How do selectors really work?

```
h1 {
	color: gray;
}
```

* ``h1`` - is called the selector here
* ``color: gray;`` the style is applied to the elements described by the selector
* ``h1, h2 { ...`` - Another selector, applying style to ``<h1>`` and` ``<h2>` nvb

## Creating CSS files

* create a file with suffix *.css

## Linking from HTML to an external stylesheet

```
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<title>page title</title>
		<link type="text/css" rel="stylesheet" href="stylesheet.css">
	</head>
	<body>
	</body>
</html>
```

* you don't need the style element anymore

## <link> element

``<link type="text/css" rel="stylesheet" href="stylesheet.css">``

* use the link element to link in external information
* the type of this information is "text/css" - in other words, a CSS stylesheet. As of HTML5, you don't need this anymore (it's optional), but you may see it an older pages.
* the rel attribute specifies the relationship between the HTML file and the thing you're linking to. We're linking to a stylesheet, so we use the value "stylesheet".
* ``<link>`` is a void element. It has no closing tag.

## Style inheritance

* nested elements inherit some styles of their parent element
* Moving styles to the body sets it for the entire page

## Overriding inheritance

* just apply a specific rule for the sub-element

## classes

``<p class="classname">some text</p>``

* adding class attribute to an element; will add that element to a class
* select that class in CSS

NOTE: elements can in more than one class

``<p class="classname anotherclass yetanotherclass">``

## Creating a class selector

```
p.classname {
	color: green;
}
```

* select the element in the class first
* use a "."to specify a class
* last is the class name

For a general class, just add a classname:

```
.classname {
	color: green;
}
```

## The world's smallest and fastest guide to how styles are applied

* First, do any selectors select your element? (check if there's a selector in your CSS that selects your element; that would be the value for your element
* What about inheritance? If there's no selector matching your element, you rely on inheritance; look at their parents.
* Struck out again? Then use the default. (if no inherited value is found, you rely on the browsers default)
* What if multiple selectors select an element? When multiple selectors match an element, your may have a *conflict* with the value. The most specific (detailed) selector will be applied.
* And if we still don't have a clear winner? The last listed class in the CSS file will be applied. ``<p class="red green blue">`` - assume same order in CSSS, blue will be applied.

## CSS Properties

* color - set the font color of text elements
* font-weight - controls the weight of text. use it to make text bold
* left - tell an element how to position its left side
* line-height - set space between lines in a text element
* top - controls the position of the top of the element
* letter-spacing - set the spacing between letters
* background-color - controls the background color of an element
* border - puts a border around an element (solid, ridged, dotted, ...)
* padding - space between the edge of an element and its content
* font-size - makes text bigger or smaller
* text-align - align text to the left center or right
* font-style - use this for italic or oblique text
* list-style - change how list items look in a list
* background-image - put an image behind an element.

## Bullet Points

* CSS contains simple statements, called rules.
* Each rule provides the style for a selection of HTML elements.
* A typical rule consists of a selector along with one or more properties and values
* The selector specifies which elements the rule applies to.
* Each property declaration ends with a semicolon
* All properties and values in a rule go between {}
* You can select any element using its name as the selector
* By separating element names with commas, you can select multiple elements at once.
* One of the easiest ways to include a style in HTML is the ``<style>`` tag.
* For HTML and for sites of any complexity, you should link to an external stylesheet.
* The ``<link>`` element is used to include an external stylesheet.
* Many properties are inherited. For instance, if a property that is inherited is set for the ``<body>`` element, all the ``<body>`` child elements will inherit it.
* You can always override properties that are inherited by creating a more specific rule for the element you'd like to change.
* Use the class attribute to add elements to a class
* Use a "." between the element name and the class name to select a specific element in that class
* Use ."classname" to select any elements that belong to the class
* You can specify that an element belongs to more than one class by placing multiple class names in the class attribute with spaces between the names.
* You can validate your CSS using the W3C validator, at http://jigsaw.w3.org/css-validator
