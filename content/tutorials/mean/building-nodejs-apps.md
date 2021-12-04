---
title: "3. Building Nodejs Apps"
slug: building-nodejs-apps
date: 2021-06-18T10:40:14+01:00
draft: false
author: Michael Borgmann
year: "2021"
month: "2021/06"
sidebar:
- "[1. Full Stack Development](/tutorials/mean/full-stack-development/)"
- "[2. MEAN Stack Architecture](/tutorials/mean/mean-stack-architecture/)"
- "[3. Building Node.js Apps](/tutorials/mean/building-nodejs-apps/)"
- "[4. MVC Architecture](/tutorials/mean/mvc-architecture/)"
- "[4.1 Setting up Bootstrap](/tutorials/mean/setting-up-bootstrap/)"
- "[4.2. Deploy on Heroku](/tutorials/mean/deploy-on-heroku/)"
- "[5. Static Pages](/tutorials/mean/static-pages/)"
- "[6. Building the Data Model with MongoDB and Mongoose](/tutorials/mean/building-the-data-model-with-mongodb-and-mongoose/)"
---

Node.js and Express build the base of any MEAN app, so let's start with that.

<!--more-->

## Setting up a MEAN Project

X Installing Node.js (and NPM)

You can either download [Node.js](https://nodejs.org), or for macOS install it by [Homebrew](https://brew.sh):

`$ brew install node`

This will also install the Node.js package manager [npm](http://npmjs.com), which enables you to install additional Node.js modules to your app. After a successful installation you can check their versions:

```
$ node --version
$ npm --version
``

X Install Express

To create an Express app you can install the Express generator.

`$ npm install -g express-generator`

of if it fails due to permissions, use

`$ sudo npm install -g express-generator`

To check the version of Express, use

`$ express --version`

X Setup package.json

Every Node app should have a [package.json](https://docs.npmjs.com/creating-a-package-json-file) file, containing metadata about the project, and required packages by the app.

You can generate one using:

`$ npm init`

X Setup an Express app

However, to create an Express app you should use:

`$ express`

This will install a basic Node.js app with Express.

However, you can configure Express and specify:

* The HTML template: `--view=pug|ejs|hbs`
* The CSS preprocesor : `--css=[sass|less|stylus`
* Create a .gitignore: `--git`

As example, installing Express with [Pug](https://pugjs.org), [less](http://lesscss.org), and [gitignore](https://git-scm.com/docs/gitignore):

`$ express --view=pug --css=sass --git`

The newly created Express app comes along with a package.json and some folders, building the base of the app. However, you still need to install the packages:

`$ npm install`

X Run the Express App

Start your freshly created Express app from the terminal:

`$ DEBUG=app:* npm start`

Open your browser and see it in action at `http://localhost:3000`.

X Install nodemon

A Node.js app is compiled, and if you make changes to the app, you have to restart it. This can get annoying while developing when changing code. Instead of restarting yourself, you can use a monitoring service to detecting changes, which restart the app automatically then. One of these services is [nodemon](https://nodemon.io), and you can install it npm:

`$ npm install -g nodemon`

Now you can launch your app once, and don't need to restart it each time you make changes to your code:

`$ nodemon`

## References

* [Node.js](https://nodejs.org)
* [Homebrew](https://brew.sh)
* [npm](http://npmjs.com)
* [package.json](https://docs.npmjs.com/creating-a-package-json-file)
* [Pug](https://pugjs.org)
* [Stylus](https://stylus-lang.com)
* [ejs](https://ejs.co)
* [Sass](https://sass-lang.com)
* [less](http://lesscss.org)
* [gitignore](https://git-scm.com/docs/gitignore)
* [nodemon](https://nodemon.io)
