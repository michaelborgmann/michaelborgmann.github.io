---
title: "HTML Markup - Modern HTML (12/13)"
date: 2021-06-22T14:28:11+01:00
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

Is ``<div>`` really a good structure? Much of the new HTML5 markup is aimed to recognize how people structure their pages, and providing markup that is more specific

<!--more-->

* ``<header>`` - content that goes at the top of the page or the top of a section of the page
* ``<time>`` - can contain a date or time or both
* ``<nav>`` - contains content meant for navigation links in the page
* ``<footer>`` - content that goes at the bottom of the page, or the bottom of a section of the page.
* ``<aside>`` - contains content that is supplemental to page content, like a callout or sidebar
* ``<section>`` - a thematic grouping of content, typically with a header and possibly a footer.
* ``<article>`` - represents a self-containt composition in a page, like a blog post, user forum post, or newpaper article
* ``<video>`` - used to add video media to your page.

Don't forget to update your CSS after replacing ``<div>`` with one of the elements.

## The ``<time>`` elements

```
<time datetime="2012-02-18">2/18/2012</time>
```

* The datetime attribute is required if the content of the element isn't written using the official Internat date/time format
* If you're using the datetime attribute to specify a date and/or a time, then you can write whatever you want as the content for the element. Most often, that will be some date- or time-relateed text, like "Febuary 18, 2012" or even "yesterday" or "now".
* "2012-02-18" is the official Internet format for specifying dates with a day, month, and year.
* Some other ways to express dates and ties:
	** 2012-02
	** 2012
	** 2012-02-18 09:00
	** 2012-02-18 18:00
	** 05:00
	** 2012-02-18 05:00Z
* If you use "Z" after the date and time, then it means UTC time (UTC=GMT)

## The ``<video>`` element

```
<video controls autoplay width="512" height="288" src="video/tweetsip.mp4"></video>
```

While it's agreed on what the ``<video>`` element looks like, not so the actual formats:

* Safari: H.264, *.mp4
* Chrome: WebM, ``src="video/tweetsip.webm"``
* Firefox, Opera: ``src=video/tweetsip.ogv"``

* ``controls`` supply controls for controlling the playback
* ``autoplay`` start playback upon page load
* ``width``, ``height`` size of video on page
* ``poster="img/poster.png"`` optional poster image to show when video isn't playing
* ``id="video"`` add an id for stylin
* ``src`` source location of the video
* ``preload`` control for how video loads
* ``loop`` loop video

The HTML5 specification allows for any video format. It is the browser implementation that determines what formats are actually supported

How to juggle these formats:

```
<video controls autoplay width="512" height"288"
	<source src="video/tweetsip.mp4">
	<source src="video/tweetsip.webm">
	<source src="video/tweetsip.ogv">
	<p>Sorry, your browser deon't support the video element</p>
</video>
```

If that's not enough, yu can help your browser by giving it more information about the MIME type and codecs:

```
<source src="video/tweetsip.mp4" type='video/mp4; codecs="avc1l42E01E, mp4a.40.2"'>
<source src="video/tweetsip.webm" type='video/vp8; codecs="vp8, vorbis"'>
<source src="video/tweetsip.ogv" type='video/ogg; codecs="theora, vorbis"'>
```

* type is an optional attribute that is a hint to the browser to help it figure out if it can play this kind of file
* This is the MIME type of the video file. It specifies the container format
* The codecs parameter specifies which codecs were used or encoding the video and autio to create the encoded video file
* ``theora`` The video codec
* ``vorbis`` The audio codec

## Bullet Points

* The container is the file format that's used to package up the video, audio and metadat information. Common container formats include: MP4, WebM, Ogg, and Flash Video
* The codec is the software used to encode and decode a specific encoding of video or audio. Popular web codecs include: Ht.264, P8, Theora, AAC, and Vorbis
* The browser decides what video it can decode. Not all browser makers agree, so if you want to support everyone, you need multiple encodings.

## Elements

* ``<aside>`` - conent aside from the main content (sidebar, pullquote)
* ``<mark>`` - highlight bits of text
* ``<audio>`` - include sound content
* ``<time>`` - time or date
* ``<progress>`` show progress on tasks
* ``<footer>`` - footer of section or document
* ``<meter>`` - display a measurement
* ``<article>`` - news article or blog post; self-contained content
* ``<canvas>`` - display graphics and animations drawn with JavaScript
* ``<section>`` - major sections of your document
* ``<header>`` - section headers or page header
* ``<video>`` - video conents
* ``<nav>`` - link groups for navigation
* ``<figure>`` - define self contained content like a photo, a diagram or a code listing

## Bullet Points

* HTML5 added several new elements to HTML
* ``<section>``, ``<article>``, ``<nav>``, ``<header>``, and ``<footer>``are all new elements to help you structure your page, and add more meaning than if you use ``<div>``.
* ``<section>``is for grouping related content.
* ``<article>``is for self-contained content like blog posts, forum posts, and news articles.
* ``<aside>``is for content that is not central to the main content of the page, such as callouts and sidebars.
* ``<nav>`` is for grouping site navigation links.
* ``<header>`` groups content such as headings, logos, and bylines that typically go at the top of a page or section.
* ``<footer>`` groups content such as document information, legalese, and copyright that typically go at the bottom of a page or section.
* ``<time>`` is also a new element in HTML5. It is used to mark up times and dates.
* ``<div>`` is still used for structure. It is often used to group elements together for styling purposes or to create structure for content that deosn't fit into one of the new strucutre-related elements in HTML.
* Older browsers don't support new HTML5 elements, so be sure you know the browsers your primary audience will be using to access your web page, and don't use the new elements until you're sure they will work for your audience.
* ``<video>``is a new HTML element for adding video to your page.
* A video codec is the encodeing used to create the video file. Poular codecs include h.264, Vp8, and Theora.
* A video container file contains video, audio, and metadata. Popular container formats include MP4, OGG, and WebM.
* Provide multiple video source files to be sure your audience can view your video files in their browsers.
