---
title: "Full Stack Development (1/10)"
date: 2021-06-18T10:39:36+01:00
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

In web development, full-stack refers to all parts of a web application, featuring the client and server side - frontend and backend.

<!--more-->

Since the advent of the Internet web development also matured a lot. Beside of simple HTML many technologies were introduced, and making web apps can be a lot of work. Today, many technology stacks exist for web development.

### Why Becoming a Full-Stack Developer

As full-stack developer you will:

* be able to build database-driven applications,
* understand the big picture and how pieces fit together
* move around more freely
* be more independent to others
* add a skill to offer more services.

As cool as it sounds, becoming a full-stack developer is hard, and also keeping up with the trends.

### MEAN Stack

The MEAN stack is a pure JavaScript stack, compiling some of the best modern web technologies into a flexible stack:

* [MongoDB](https://www.mongodb.com) - the database
* [Express](http://expressjs.com) - the web framework
* [Angular](https://angular.io) - the front-end framework
* [Node.js](https://nodejs.org) - the web server

## Node.js - The web server/platform

Node.js is a JavaScript runtime build on [Chrome's V8 JavaScript engine](https://v8.dev/), and builds the foundation of the stack. With Node.js you can create your own web server to provide services being consumed by web applications.

### Single threaded & nonblocking

In contrast to a traditional multithreaded web server, Node.js is single-threaded, and processes incoming requests asynchronously in a nonblocking way, processing a task until it's completed without blocking the thread.

### NPM

Node.js comes with its own packet manager - [npm](https://www.npmjs.com) - providing the ability to install additional node modules/packages to along your application.

However, Node.js is a platform and not a web server. Thus you can build a server setup unlike other web servers, which also makes running websites harder.

## Express - The framework / middleware

Express is a Node.js web application framework that provides features for web and mobile applications.

### Server setup

It makes developers life easier by abstracting away typical tasks setting up a web server, and acts as middleware - the glue between service and application.

### Routing

A core feature of Express is routing, and it provides an interface for incoming client requests of a certain endpoint and how it responds. Wether it serves static HTML, or reads and writes from a database.

### Template engine

Express supports popular template engines - as [Pug](https://pugjs.org/api/getting-started.html) - which simplifies building web pages. Ultimately, templates will be be compiled to HTML to be rendered by the browser.

### Sessions

HTML is a stateless protocol, and Node.js has no concept of storing session states. Again, Express comes to the rescue to to create a personalised experience with sessions by identifying visitors through multiple requests.

## MongoDB - The database

### Document store

MongoDB is a document based NoSQL database, which means it stores data in [JSON](https://www.json.org)-like documents... instead of traditional rows and columns. This serves surprisingly well for modern web and mobile apps.

MongoDB documents are stored in [BSON](http://bsonspec.org) (binary JSON)

### Mongoose

As flexible as MongoDB is in storing data in documents, applications need to structure data. With [Mongoose](https://mongoosejs.com) you can structure and model data inside of your web application.

## Angular - The front-end framework

With Node.js, Express, and MongoDB you can already build fully functioning, data-driven web applications, but with Angular you can build modern, efficient, and sophisticated single-page-applications. Angular enables you to to move processing logic to the browser, leaving the server to just pass data.

### Data binding

Unlike [jQuery](https://jquery.com), which actions after the HTML has been loaded by the browser. Angular instead  builds the HTML and also updates the data in a two-way data binding, updating the model and changing what's displayed.

### Single-Page-Applications

Basically, an SPA runs the web application inside the browser and never fully reloads the page. Logic, data processing, user flow, and template delivery can be managed in the browser. The browser is doing the hard work, not the server, which only serves static files and data on request. This can result in fewer server calls and reduce latency, providing a better user experience.

### TypeScript

Angular is [TypeScript](https://www.typescriptlang.org) based, which is a superset of the JavaScript standard [ECMAScript 6](https://www.ecma-international.org/publications/standards/Stnindex.htm#Software_Engineering_and_Interfaces).

## Additional Technologies

The MEAN stack provides everything to create data-rich interactive web applications, but you may need need additional technologies along the way.

### Twitter Bootstrap

Websites have to be rendered on any device size today. [Bootstrap](https://getbootstrap.com) is a  framework to help building responsive user interfaces rapidly, in a mobile-first approach.

### Git

A version control system is an essential tool in software development, and [Git](https://git-scm.com) is a powerful tool of choice.

### Heroku

Hosting Node.js applications can be hard, and many traditional hosts have limited or no support hosting at all.

To host your Node.js app, you either need an own server, or a service specifically for hosting Node.js.

[Heroku](https://www.heroku.com) makes deploying Node.js apps extremely simple, they are essentially Git repositories. They also provide a free tier.

## References

* [MongoDB](https://www.mongodb.com)
* [Express](http://expressjs.com)
* [Angular](https://angular.io)
* [Node.js](https://nodejs.org)
* [Chrome's V8 JavaScript engine](https://v8.dev/)
* [npm](https://www.npmjs.com)
* [Pug](https://pugjs.org/api/getting-started.html)
* [JSON](https://www.json.org)
* [BSON](http://bsonspec.org)
* [Mongoose](https://mongoosejs.com)
* [jQuery](https://jquery.com)
* [TypeScript](https://www.typescriptlang.org)
* [ECMAScript 6](https://www.ecma-international.org/publications/standards/Stnindex.htm#Software_Engineering_and_Interfaces)
* [Bootstrap](https://getbootstrap.com)
* [Git](https://git-scm.com)
* [Heroku](https://www.heroku.com)
