---
title: "Mean Stack Architecture (2/10)"
date: 2021-06-18T10:39:58+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
series: Getting MEAN
categories:
- Web
tags:
- MEAN
---

The MEAN stack is powerful, but it's no magic bullet which fits everywhere.

<!--more-->

X MEAN Stack Architecture

A typical MEAN stack architecture is made of a REST API build with MongoDB, Node.js, and Express, feeding a SPA build with Angular.

X REST API

**REST**: REpresentational State Transfer

REST is an architectural style, defining constrains to be used on web services, providing interoperability between web services, and was first presented by [Roy Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm).

Guiding Constraints:

* **Client-Server**: Separating concerns of UI from data storage.
* **Stateless**: A client request contains all information to be serviced, and also holds the session state.
* **Cacheable**: A response requires the data to be label implicitly or explicitly as cacheable or non-cacheable.
* **Uniform Interface**: By defining a uniform interface, the client decouples from service implementation. To obtain a uniform interface, REST is defined by four constraints:
	* resource identification
	* resource manipulation through representation
	* self-descriptive messages
	* Hypermedia as the Engine of Application State ([HATEOAS](https://en.wikipedia.org/wiki/HATEOAS))
* **Layered-System**: Additional layers of different behaviour between client-server without affecting the communication.
* **Code on demand**: Extending client functionality by providing downloadable code - as precompiled applets or client-side scripts.

**API**: Application Programming Interface

An API defines a communication interface between software.

X When not to use SPAs

**Crawlability**: Most search engines will not execute or even download JavaScript code, only looking up for the HTML. A solution could be to make a separate HTML, mirroring the SPA content. This also affects SEO.

**Analytics integration**: Analytic tools relying on page loading can only track the initial SPA page load. Any further tracking has to be done by the app itself.

**Page load speed**: Loading SPAs is slower than just pushing HTML by a server-based application. This can be speeded up with caching and lazy-loading modules.

X Hybrid MEAN Architecture

Depending on you needs, you may consider a hybrid architecture, instead of an all-in-one solution, and split up your app into two - a server-base Express app, and a single-page Angular app.

* A content-rich express app, with low interaction but quick page loading, which can be easily shared.
* A feature-rich Angular app, with high interaction and quick response time, which is more private.

X Building an API

Of course you could easily build a Node.js app which directly communicates with the database, but this with would tightly couple it. A better solution is to build an API, which can also be consumed by different apps, e.g. by Node.js, Angular, and mobile apps.

X Rapid Prototyping

A reasonable approach to craft your MEAN app could involve following steps:

1. Build a static site
2. Design data models and creating the database, feeding the static site
3. Build an API interfacing serving request to the database
4. Use the API to feed your website
5. Build an interactive SPA using Angular, feed by data through the API.

X Hardware Architecture

For development you can run your app and service on your local machine, without using a public server. This will change when deploying your app for publicly to the Internet - for production you'll have a couple of options:

* Run all your services on one server.
* Run your database on a separate server than your app.
* Run your database, API, and application on different servers.
* Run multiple instances (clusters) for each of those components.

## Resources
* [Architectural Styles and
the Design of Network-based Software Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)
