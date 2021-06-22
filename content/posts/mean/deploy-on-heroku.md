---
title: "Deploy on Heroku (4.2/10)"
date: 2021-06-18T10:40:53+01:00
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

*Create and Setting up a MEAN project III*

Going live with your Node app and deploying it to your production server can be difficult. To make life easier you can consider using a PaaS provider, and [Heroku](https://www.heroku.com) is just one option. Beside paid services they also offer a free service, which should be enough for prototyping and development.

<!--more-->

## Setup Heroku

Go to [Heroku](https://www.heroku.com) and sign up for a free account. then install the Heroku CLI:

`$ npm install -g heroku`

or optionally with [Homebrew](https://brew.sh):

`$ brew tap heroku/brew && brew install heroku`

To check the installed Heroku version, type:

`$ heroku --version`

Ultimately, you have to login, connecting your account:

`$ heroku login`

This opens the browser for confirmation, but you can also do everything from the terminal:

`$ heroku login -i`

As Heroku can run apps in different environments, you should at least specify the version of Node.js:

`$ node --version`

which currently outputs `v14.7.0`. Add your not

```
"engines": {
    "node": "~14.7.0"
}
```

The preceding tilde (~) indicates updating the patch version, a caret (^) indicates updating the minor versions.

In addition, Heroku uses a [Procfile](https://devcenter.heroku.com/articles/procfile) which declares the process type and how to start your application. Create a `Procfile` in the project's root directory, and add the following to tell Heroku starting a web process and running the app:

`web: npm start`

## Run Locally

You can verify your Heroku app and setup locally before pushing and deploying. Execute the following command, and watch your app in the browser at `http://localhost:5000`:

`$ heroku local`

## Going Live

X Git

Heroku uses [Git](http://git-scm.com/) to deploy apps. If you haven't already put your code under version control using Git, you have to in order being able to deploy on Heroku:

```
$ git init
$ git add -all
git commit -m "Initial import"
```

X Create a Heroku Application

With your Git repository set, you are ready to make a Heroku app of it:

`$ heroku create`

This should create an app with a random name, and a git repository to push your code to for deployment:

```
Creating app... done, ⬢ cryptic-retreat-90105
https://random-name-12345.herokuapp.com/ | https://git.heroku.com/random-name-12345.git
```

## Deployment

As Heroku uses Git for deployment, all you have to do is pushing your code to your Heroku Git repository:

`$ git push heroku master`

You should be able to view your app life now:

`$ heroku open`

## References

* [Heroku](https://www.heroku.com)
* [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
* [Homebrew](https://brew.sh)
* [Procfile](https://devcenter.heroku.com/articles/procfile)
* [Git](http://git-scm.com/)
