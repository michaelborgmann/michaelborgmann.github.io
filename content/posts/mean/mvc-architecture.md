---
title: "Mvc Architecture (4/10)"
date: 2021-06-18T10:40:25+01:00
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

*Create and Setting up a MEAN project I*

Mode-View-Controller is a software architecture pattern to decouple data, view, and logic.

<!--more-->

This article will not explain MVC, but explore implementations for the MEAN stack

## Modifying Express for MVC

An MEAN app build with MVC could be like:

* Input request
* Route request to a controller
* Controller may request to the model
* Model response to controller
* Controller merges view and data into a response
* Controller sends response to requester

X Modify Folder Structure

A fresh Express app should have a `views` and `routes` folder, but misses models and controllers:

1. Add a new folder for your Express MVC app, e.g. `app_server`
2. Move `views` and `routes` from the app root into the new folder
3. Create two new folders inside, named `models`and `controllers`

The new folder structure shows the intend to use MVC, but the app is broken now needs to be fixed by adopting the new structure.

X Update Views

First, update the Express app about having moved `views` and `routes` - edit `app.js` and change:

`app.set('views', path.join(__dirname, 'views'));`

... to ...

`app.set('views', path.join(__dirname, 'app_server','views'));`

X Update Routes

As `models` is also relocated you have to update it too - edit `app.js` and change:

```
var indexRouter = require('./routes/index');
var usersRouter = require('./routes/users');
```

... to ...

```
var indexRouter = require('./app_server/routes/index');
var usersRouter = require('./app_server/routes/users');
```

X NOTE

You should consider using `const` instead of `var`, or integrating [Babel](https://babeljs.io).

X Split Controllers from Routes

Express defines controllers with routes, but for MVC controlling app logic and routing URL requests should be decoupled.

Basically, routing determines how an app responds to a request from a particular endpoint for a specific HTTP method (GET, POST, PUT, DELETE, etc.). In Express, this looks like `app.METHOD(PATH, HANDLER)`. A concrete example could be like:

```
app.get('/', function (req, res) {
	res.render('index', { title: 'Express' });
})
```

The anonymous function is the controller code.

The `res` object sends a response to the client (`res.send`, `res.render`, etc.), and terminates the request - otherwise the client would hang.

Ultimately, to separate controllers from routers, extract the controller into a separate Node module; a separate source file exposing functions with `module.export`, which are included to the original file with `require`.

Create your controller file inside `app_server/controllers` - e.g. named `main.js` - and cut out the controller code from the `index.js` router. Don't forget to expose the module function at the end:

```
/* GET homepage */

const index = (req, res) => {
	res.render('index', { title: 'Express' });
};

module.exports = {
	index
};`
```

Now you can `require` the controller module into the `app_server/routes/index.js` file, and use the exposed method:

```
var express = require('express');
var router = express.Router();

const controller = require('../controllers/main');

/* GET home page. */
router.get('/', controller.index);

module.exports = router;
```


## Resources

* [Babel](https://babeljs.io)
* [Express Routing](https://expressjs.com/en/guide/routing.html)
