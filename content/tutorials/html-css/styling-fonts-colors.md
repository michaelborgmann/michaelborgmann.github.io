---
title: "8. Styling Fonts Colors"
slug: styling-fonts-colors
date: 2021-06-18T10:15:41+01:00
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

Styling with fonts and colors - Expanding Your Vocabulary

<!--more-->

*Almost originally from HF*

## Text and fonts from above

* In CSS, fonts are divided into font families from which to specify the fonts to use
* Some fonts are preinstalled

* font-size: set size of font (14px, 21px, ...)
* color: set text color (aqua, black, blue, fuchsia, gray, green, lime, maroon, navy, olivia, purple, red, silver, teal, white, yellow
* font-weight: set font weight (lighter, normal, bold, bolder)
* text-decoration: add text decoration (none, underline, overline, line-through

## What is a font family?

Five Font families:
* sans-serif (without serifs; more readable on computer)
* serif (with decorative barbs and hooks)
* monospace (fonts with constant width)
* cursive (looks handwritten)
* fantasy (stylized fonts)

## Specifying font families using CSS

```
body {
	font-family: Verdana, Geneva, Arial, sans-serif;
}
```

* specify more than one font using the font-family property
* always put a generic font-family name at the end
* The browser checks for available fonts, from first to last

## How do deal with having different fonts?

* You cannot control which fonts are installed on a computer

## How Web Fonts works

1. The browser retrieves an HTML page
2. The browser then retrieves the Web Font files needed for the page
3. With the font retrieved, the browser uses the font when it displays the page

* Woff - emerging as standard for web fonts

## How to add Web Fonts to your page

1. Find a font
2. Make sure you have all the formats of the font you need. The @font-face CSS rule is pretty much standard today, but the fonts itself not. The best supported format is web open font format. Maybe offer an alternative font for older browser (TrueType)
3. Place your font files on the web
4. Add the @font-face property to your CSS

```
@font-face {
	font-family: "Emblema One";
	src: url("./EmplemaOne-Regular.woff"),
			 url("./EmplemaOne-Regular.ttf");
}
```

5. Use the font family name in your CSS

```
h1 {
	font-family: "Emblema One", sans-serif;
}
```

6. Load the page!

## @ in CSS

* Think of @font-face as a build-in CSS rule, rathern than a rule that acts like a selector
* Instead of selecting an element, @font-face allows to retrieve a Web font, and assign it to a font-family name.
* The @ at the beginning is a good clue this isn't an ordinary CSS rule.

### @ Build-in rules

Other common build-in rules are @import, which allows to import other CSS files and @media, which allows to create CSS rules that are specific to certain media types, like a printed page vs. a desktop screen vs. mobile phone.

## Adjusting font sizes

* by pixels: ``font-size: 14px;``
* specify size in percent relative to another font size:

```
body {
	font-size: 14px;
}

h1 {
	font-size: 150%;
}
```

* by scaling factor, relative to parent element

```
body {
	font-size: 14px;
}

h2 {
	font-size: 1.2em;
}
```

* by keywords, and the browser applies defaults: xx-small, x-small, small, medium, large, x-large, xx-large

```
body {
	font-size: small;
}
```

## How to specify font sizes?

How to specify font sizes that will give consistent results for most browsers:

1. Choose a keyword (recommended small or medium), and specify it as font size the body rule, making this the default size for the page
2. Specify the font sizes of your other elements relative to the body font size, either using em or percentages

By defining fonts relative to the body font size, it's easy to change the font sizes in the web page simply changing the body font size.

## Changing font's weight

* ``font-weight: bold;``
* ``font-weight: normal;``
* also bolder and lighter, making text style a little bolder or lighter relative to its inherited value. Rarely used
* by property (100-900): ``font-weight: 100;``

## Adding style to fonts

* italic: ``font-style: italic;``
* oblique (when italic is not available, the browser applies a slant): ``font-style: oblique;``

Italic and oblique styles are two styles that give fonts a slanted appearance.

Unless you can control the fonts and browsers your visitors are using, you'll find that sometimes you get italic, and sometimes oblique, no matter which style you specify.

So just go with italic and don't worry about the differences (you probably can't control them anyway).

## How do web colors work?

* by name: ``background-color: silver

Color Names (basic color names):

* Aqua
* Black
* Blue
* Fuchsia
* Gray
* Green
* Lime
* Maroon
* Navy
* Olive
* Purple
* Red
* Silver
* Teal
* White
* Yellow

* by RGB in percentage: ``background-color: rgb(80%, 40%, 0%);``
* by RGB in values (0-255): ``background-color: rgb(204, 102, 0);``
* by hex codes: ``background-color: #cc6600;``

## Web Colors

A chart can be found at [Wikipedia](http://en.wikipedia.org/wiki/Web_colors)

## Tags

* color: #cc5500;
* ``text-decoration: underline`` (line-through, underline, overline, none)

## Bullet Points

* CSS gives you lots of control over the look of your fonts, including properties like font-family, font-weight, font-size, font-style.
* A font-family is a set of fonts that share common characteristics.
* The font families for the Web are serif, sans-serif, monospace, cursive, and fantasy. Serif and sans-serif fonts are most common.
* The fonts that your visitors will see in your web page depend on the fonts they have installed on their own computers, unless you use Web Fonts.
* It's a good idea to specify font alternatives in your font-family CSS property in case your users don't have your preferred font installed.
* Always make the last font a generic font like serif or sans-serif, so that the browser can make an appropriate substitution if no other fonts are found.
* To use a font that your users may not have installed by default, use the @font-face rule in CSS.
* Font sizes are usually specified using px, em, %, or keywords.
* If you use pixels ("px") to specify your font size, you are telling the browser how many pixels tall to make your letters.
* em and % are relative font sizes, so specifying your font size using em and % means the size of the letters will be relative to the font size of the parent element.
* Using relative sizes for your fonts can make your pages more maintainable.
* Use the font size keywords to set the base font size in your body rule, so that all browsers can scale the font sizes if users want the text to be bigger or smaller.
* You can make your text bold using the font-weight CSS property.
* The font-style property is used to create italic or oblique text. Italic and oblique text is slanted.
* Web colors are created by mixing different amounts of red, green, and blue
* If you mix 100% red, 100% green, and 100% blue, you will get white.
* If you mix 0% red, 0% green, and 0% blue, you will get black.
* CSS has 16 basic colors, including black, white, red, blue, and green, and 150 extended colors.
* You can specify which colors you want using percentages of red, green, and blue, using numerical values of 0-255 for red, green, and blue, or using a color's hex code.
* An easy way to find the hex code of a color you want is to use a photo editing application's color picker or one of many online web tools.
* Hex codes representing colors have six digits, and each digit can be from 0-F. The first two digits represent the amount for , the second two the amount of green, and the last two the amount of blue.
* You can use the text-decoration property to create an underline for text. Underlined text is often confused as linked text by users, so use this property carefully.
