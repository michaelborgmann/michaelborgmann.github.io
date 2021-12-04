---
title: "5. Adaptive Layouts With Media Queries"
slug: adaptive-layouts-with-media-queries
date: 2021-06-18T11:00:09+01:00
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

- responsive website = adaptive layout
- viewport = browser's viewable area

<!--more-->

Write styles for smallest screen, then provide override styles in *media queries* triggered on *viewport* threshold.

Front-end developers need to focus on the *layout viewport* (*actual viewport*). The layout viewport tells the browser, "pretend that I'm 980px wide and then draw the page".

Users are concerned with a mobile browser's *visual viewport* - the thing to pinch to zoom in and out on a page.
