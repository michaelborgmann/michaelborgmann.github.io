---
title: "5. Adding Media"
slug: adding-media
date: 2021-06-18T10:02:07+01:00
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

Adding image to your pages - Meeting the Media

<!--more-->

*Almost originally from HF*

## How the browser works with images

1. The browser retrieves the HTML file
2. Browser reads the HTML file, displays it, and sees it has images to retrieve
3. One image after another

## Image Formats

* Use JPEG for photos and complex graphics
* Use PNG or GIF for images with solid colours, logos, and geometric shapes.

## <img>

``<img src="filename.png">``

* ``<img>`` is an inline element and doesn't cause linebreak to be inserted before or after it.
* The src attribute specifies the location of an image file to be included in the display of the web page
* ``<img>`` is a void element

## Always provide an alternative

Give the visitor some indication of what information is in the image using the ``<img>`` elemnt's alt attribute

```
<img src="url/filename.gif" alt="Description of Image">
```

## Size of Image

With the width and height attributes tell the browser, up front, the size of an image in your page.

```
<img src='url/filename.png width="48" height="100">
```


## Making links out of images

Put the ``<img>`` tag inside an ``<a>`` tag.

```
<a href="uri">
	<img src="filename.jpg" alt="description">
</a>
```

## Bullet Points

* Use the ``<img>`` element to place images in your web page.
* Browsers treat ``<img>`` elements a little differently than other HTML elements; after reading the HTML page, the browser retrieves each image from the web server and displays it.
* If you have more than a couple of large image on a web page, you can make your web page more usable faster to download by creating thumbnails -- small images that the user can click on to see the large version of the image.
* The ``<img>`` elements is an inline element which means that the browser doesn't put a linebreak before or after an image.
* The src attribute is how you specify the location of the image file. You can include images from your own site using a relative path in the src attribute, or images from other sites using a URL.
* The alt attribute of an ``<img>`` element is a meaningful description of the image. It is displayed in some browsers if the image can't be located, and is used by screen readers to describe the image for the visually impaired.
* A width of less than 800 pixels is a good rule of thumb for the size of photo images in a web page. Most photo images that are created by digital cameras are too large for web pages, so you'll need to resize them.
* Phtoshop Elements is one of many photo editing applications you use to resize your images. You can also use one of many free online tools to resize images. Just search for "free online image editor."
* Images that are too large for the browser make web pages difficult to use and slow to download and display.
* JPEG, PNG, and GIF are the three formats for images that are widely supported by web browsers.
* The JPEG format is best for photographs and other complex images
* The GIF or PNG format is best for logos and other simple graphics with solid colours, lines, or text.
* JPEG images can be compressed at a variety of different qualities, so you can choose the best balance of quality and file size for your needs.
* The GIF and PNG image formats allow you to make an image with a transparent background. If you put an image with a transparent background in a web page, what's behind the image, such as the backgroun color of the page, will show through the transparent parts of the image.
* GIF and PNG are lossless formats, which means the file sizes are likely to be larger than JPEG.
* PNG has better transparency control than GIF and allows many more colors than GIF, which is limited to 256.
* PNG has three different size options: PNG-24 (supports millions of colors), PNG-16 s(supports thousand of colors), and PNG-8 (supports 256 colors), depending on your needs.
* In Photoshop lements, use the Matte color menu in the "Save for Web" dialog to choose the right color for softening the edges of your transparent PNG or GIF image.
* Images can be used as links to other web pages. To create a link from an image, use the ``<img>`` element as the content of an ``<a>`` element, and put the link in the href attribute of the ``<a>`` element.
