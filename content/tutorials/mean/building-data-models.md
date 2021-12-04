---
title: "6. Building the Data Model with MongoDB and Mongoose"
slug: building-the-data-model-with-mongodb-and-mongoose
date: 2021-06-18T10:42:05+01:00
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

According to MVC, the view shouldn't contain any data, but gets the data injected by the controller, which itself shouldn't store data. The next step to separate responsibility is creating a database and a data model. For the MEAN stack this is [MongoDB](https://www.mongodb.com) with [Mongoose](https://mongoosejs.com).

<!--more-->

This process is like:

1. Make a connection to the MongoDB database
2. Define schemas and models with Mongoose
3. Add data to the database
4. Push to live environment

## Installing MongoDB

MongoDB is available for MacOS, Linux, and Windows.

X Install MongoDB for MacOS

Likely the easiest way to install MongoDB is using [Homebrew](https://brew.sh) from the official [MongoDB Homebrew Tap](https://github.com/mongodb/homebrew-brew):

First, add the tap:

`$ brew tap mongodb/brew`

Then install the MongoDB server, shell, and tools:

`$ brew install mongodb-community`

X Install MongoDB for Linux

X Install MongoDB for Windows

## Connect an Express App to MongoDB by using Mongoose

X Add Mongoose to your App

X Add a Mongoose Connection to your App

## Model the Data

X

## Defining a Mongoose Schema

X

## MongoDB Database and Shell

X

## Getting MongoDB Live

X

## References

* [MongoDB](https://www.mongodb.com)
* [Mongoose](https://mongoosejs.com)
* [Homebrew](https://brew.sh)
* [MongoDB Homebrew Tap](https://github.com/mongodb/homebrew-brew)
