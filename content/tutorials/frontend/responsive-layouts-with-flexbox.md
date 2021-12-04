---
title: "4. Responsive Layouts With Flexbox"
slug: responsive-layouts-with-flexbox
date: 2021-06-18T10:59:51+01:00
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

Responsive Layouts with Flexbox

<!--more-->

## Expanding the Interface

Mobile-first development has proven to be the best design approach: designing for small screens first, then building on that design for tablet-size screens, and finally building up to a desktop-sized design.

## Flexbox

The *flexible box model* (flexbox) dynamically specifies the flow of elements (similar to `display`, but more flexible).

When an element is a flex container, it can control how its child elements (flex items) are laid out across the *main axis* and *cross axis*.

	body {
		display: flex;
		...
	}

### Changing the flex-direction

This swaps the main and cross axes for the flex container:

	flex-direction: column;

### Flex shorthand property

A flex container distributes its space to the flex items inside of it, and distributes the space evenly if not further specified.

The `flex` property specifies how much of the available space the element will take up, and declares *grow*, *shrink*, and *basis*:

	flex: 0 1 auto;

This can be read as:

- I do not want to grow any larger
- I will shrink as needed
- Please calculate my size for me

Another example:

	flex: 1 1 auto;

The first value now means:

- I'd like to grow as much as possible

### Ordering, justifying, and aligning flex items

#### order

Reorder item to be drawn within flexbox. Default is `0` (source order). Any other value (including negative numbers, tells to draw an item before or after another item. Here, `2` tells to be drawn after any of its siblings:

	order: 2;

#### justify-content

The `justify-content` property controls how items are drawn on the main axis. With `space-between` there's an even amount of spacing around each item.

	justify-content: space-between;

Other values are:

- `flex-start` - order items from start
- `flex-end` - order items from end
- `center` - order items centered
- `space-between` - equal spacing between items
- `space-around` - equal space around items

#### align-items

Align items along the cross axis (vertically)

	align-items: center;

## Absolute and Relative Positioning

Absolutely positioned elements must have:

- `position: absolute` to take element out of *normal flow* rather than laying it out along its siblings.
- coordinates, using `top`, `right`, bottom, or left; absolute length in pixels or relative lengths in percantage
- ancestor with an explicitly declared `position`, otherwise it will be placed relative to the `<html>` element.

WARNING: Use `absolute` sparingly.

	 {
		 position: absolute;
		 top: 50px;
		 left: 200px;
	 }

Use `position: relative` to remain in normal flow. To serve as container for an absolutely positioned descendant, this must also be defined explicitly.

### absolute

	{
		position: absolute;
		bottom: -16px;
		left: 4px;
		...
	}
