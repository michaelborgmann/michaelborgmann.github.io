---
title: "11. Layout and Positioning - Arranging Elements"
slug: layout-and-positioning-arranging-elements
date: 2021-06-22T12:55:54+01:00
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

Layout and Positioning - Arranging Elements

<!--more-->

```
float: right;
```

## Use the Flow

Flow is what the browser uses to lay out a page of HTML elements. The browser starts at the top of any HTML file and follows the flow of elements from top to bottom, displaying each element it encounters. And, just considering the block elements for a moment, it puts a linebreak between each on.

## Inline Elements

As block elements flow top to bottom with a linebreak between each element. Inline elements are flowed next to each other, horizontally, from top left to bottom right.

## More about flow and boxes

When the browser is placing two inline elements next to each other, it creates space between the elements

When placing two block elements, the shared margin gets collapsed together. The height of the collapsed margin is the height of the largest margin.

## To understand float, you have to understand flow

This little property is closely tied to how the browser flows elements and content onto the page.

The ``float`` property first takes an element and *floats*  it as far left or right as it can (based on the value of ``float``). It then flows all the content below it around the element. But there are more details

## How to float an element

1. Give an element an id (e.g. a paragraph element)
2. A requirement for any floating element is that it have a width
3. Float it, either left or right

```
#amazing {
	width: 200p`;
	float: right;
```

Stepping through how the browser floats:
1. From top to bottom
2. Moving the floated element; to the right, and remove paragraph from the flow; like floating on the page
3. As the floated paragraph has been removed from the normal flow, the block elements are filled in, like the paragraph isn't even there. Note: Block elements are positioned under floated element, as the floated element is no longer part of the normal flow
4. Inline elements respect the boundaries of the floated element, and flow around it.

## Moving A Sidebar

1. When you float an element, you need to move the HTML for the element directly below the element that you want it to follow, e.g. a sidebar needs to go under the header.
2. Set the width of the sidebar and float it:

```
#sidebar {
	width: 280px;
	float: right;
}
```

This would result in floating, but not two columns. One solution would be to have the left content section a right margin as width as the sidebar. But that may result in a distorted height of the sidebar and overlapping the footer.

## Solving overlap with ``clear``

You can use the ``clear`` on an element to request that as the element is being flowed ont the page, no floating content is allowed on the left, right, or both sides of the element:

```
#footer {
	clear: right;
}
```

## Liquid and frozen designs

*Liquid layouts*. expand to fill whatever width the browser resizes. These layouts are useful because by expanding they fill the space available and allow users to make good use of their screen space.

However, sometimes having layout locked when the user resizes the screen, the design still looks as it should. This is called *frozen layout*. Frozen layouts lock down the elements, frozen to the page, so they can't move

All you have to do is a tiny change. In your HTML just create another ``<div>`` wrapping all your content:

```
<body>
	<div id="content">
		<div id="header">
			...rest of HTML
		</div>
	</div>
</body>
```

Now constrain all elements and content in the new ``<div>`` to a fixed width:

```
#content {
	width: 800px;
	padding-top: 5px;
	padding-bottom: 5px;
	background-color: #675c47;
}
```

## Jello - between liquid and frozen

Jello layouts lock down the width of the content area in the page, but centre it in the browser:

```
#content {
	width: 800px;
	padding-top: 5px;
	padding-bottom: 5px;
	background-color: #675c47;
	margin-left: auto;
	margin-right: auto;
}
```

## Absolute positioning

Instead of floating a ``<div>``, it can also easily positioned absolutely with a few changes:

```
#sidebar {
	background: #efefef
	padding: 15px;
	margin: 0px 10px 10px 10px;
	position: absolute;
	top: 128px;
	right: 0px;
	width: 280px;
}
```

Don't forget to change the margin at the main section:

```
#main {
	background: #343434;
	padding: 15px;
	margin: 0px 330px; 10px 10px;
}
```

Unfortunately, you cannot fall back on the ``clear`` property to fix the overlapping footer problem, because flowed elements ignore the presence of absolutely positioned elements.

## CSS Table Display

Think of a table like a spreadsheet with rows and columns, and at the intersection a cell.

Create a ``<div>`` for the entire table and then on ``<div>`` per row. And for each column, a block level element that is replaced within the row ``<div>``.

1. Create a ``<div>`` that represents the entire table, and nest the columns and rows within that ``<div>``.
2. For each row in the table, we'll create another ``<div>`` that will contain the row content.
3. For each column, we just need a block element to act as that column. We already have two block element to use: the 'main' and 'sidebar' ``<div>``.

```
<div id="tableContainer">
	<div id="tableRow">
		<div id="main">
			...
		</div>
		<div id="sidebar">
			...
		</div>
	</div>
</div>
```

## Use CSS to Create Table Displays

1. Style the ``tableContainer`` like:

```
div#tableContainer {
	display: table;
}
```

2. Style the row:

```
div#tableRow {
	display: table-row;
}
```

3. Style the cells:

```
#main {
	display: table-cell;
	padding: 15px
	margin: 0px 10px 10px 10px;
}

#sidebar {
	display: table-cell;
	padding: 15px
	margin: 0px 10px 10px 10px;
}
```

You may have to fix spacing between header, table, and footer. Instead of having some margin, set it to 0px (for header and footer):

```
#header {
	margin: 10px 10px 0px 10px;
}

#footer {
	margin: 0px 10px 10px 10px;
}
```

Note: In contrast to HTML tables, which are to represent data, CSS display-table is a way of creating a certain kind of representation layout.

## Strategies for your CSS layout toolbox

HTML should be about structuring content, and CSS handles the layout.

**The Floating Layout**: Flow the main content around other content. This also works great for images floating within a paragraph.

**Jello Layout**: A froxen layout with a fixed-size around the content, and then making it jello by allowing the margins to expand. Many blogs do this.

**Absolute layout**:  Get back to a liquid layout, and keep content in order. Setting a sidebar to a specific width, and positioning it to the side of the main content, and making the main content expand with the width of the page.

**Table Display Layout**:

## Positioning

* ``position: absolute``
* ``z-index: 1``

## Fixed Positioning

Compared to absolute positioning, fixed positioning is pretty straightforward. You specify the position of an element, just like with absolute positioning, but the position is an offset from the edge of the browser's window rather than the page. Once place, it stays there and doesn't move, even if you scroll the page.

```
#coupon {
	position: fixed;
	top: 300px;
	left: 100px;
}
```

## Bullet Points

* Browsers place elements in a page using flow.
* Block elements flow from the top down, with a linkebreak between elements. By default, each block element takes up the entire width of the browser window.
* Inline elements flow inside a block element from the top left to the bottom right. If more than one line is needed, the browser creates a new line, and expands the containing block element vertically to contain the inline elements.
* The top and bottom adjacent margins of two block elements in the normal page flow collapse to the size of the larger margin, or to the size of one margin if they are the same size.
* Floated elements are taken out of the normal flow and placed to the left or right.
* Floated elements sit on top of block elements and don't affect their flow. However, the inline content respects the boundaries of a floated element and flows around it.
* the clear property is used to specify that no floated elements can be on the left or right (or both) of a block element. A block element with clear set will move down until is free of the block element on its side.
* A floated element must have specific width set to a value other than auto.
* A liquid layout is one in which the content of the page expands to fit the page when you expand the browser window.
* A frozen layout is one in which the width of the content is fixed, and it doesn't expand or shrink with the browser window. this has the advantage of providing you more control over your design, but at the cost of not using the browser width as efficiently.
* A jello layout is one in which the content width is fixed, but the margins expand and shrink with the browser window. A jello layout usually places the content in the center of the page. this has the same advantages as the frozen layout, but is often more attractive.
* There are four values the position property can be set to: static, absolute, fixed, and relative.
* Static positioning is the default, and places an element in the normal flow of the page.
* Absolute positioning lets you place elements anywhere in the page. By default, absolutely positioned elements are placed relative to the sides of the page.
* If an absolutely positioned element is nested within another positioned element, then its position is relative to the containing element that is positioned.
* The properties top, right, bottom, and left are used to position elements for absolute, fixed, and relative positioning.
* Absolutely positioned elements can be layered on top of one another using the z-index property. A larger z-index value indicates it is higher in the stack (closer to you on the screen).
* Fixed-position elements are always positioned relative to the browser window and do not move when the page is scrolled. Other content in the page scrolls underneath these elements.
* Relatively positioned elements are first flowed into the page as normal, and then offset by the specified amount, leaving empty the space where they would normally sit.
* Whit relative positioning, left, right, top, and bottom refer to the amount of offset from the element's position in the normal flow.
* CSS table display allows you to lay out your elements in a table-like layout.
* To create a CSS table display, use a block element for the table, block elements for the rows, and block elements for the cells. Typically, these will be ``<iv>`` elements.
* Table display is a good layout strategy for multicolumn layouts where even columns of content are needed.
