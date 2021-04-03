---
alwaysopen: true
date: "2020-08-20T16:42:11.812Z"
description: Getting started
head: <hr/>
hide:
- toc
post: "&nbsp;\U0001F44B"
title: Getting started
weight: 2
---

# Table of contents

Baserow is an open-source online database tool. Users can use this no-code platform to create a database without any technical experience. It lowers the barriers to app creation so that anyone who can work with a spreadsheet can also create a database. The interface looks a lot like a spreadsheet. Our goal is to provide a perfect and fast user experience while keeping it easy for developers to write plugins and maintain the codebase. The developer documentation contains several topics you might need as a developer.

## Getting started

New to Baserow? This is the place to start.

    Introduction: An introduction to some important concepts before using Baserow.
    API: An introduction to the REST API and information about API resources.
    WebSocket API: An introduction to the WebSockets API which is used to broad cast real time updates.
    Database plugin An introduction to the database plugin which is installed by default.

# #Guides

Need some help with setting things up?

    Local demo: Run a local demo on your computer using docker-compose.
    Install on Ubuntu: A step by step guide on how to install Baserow on an Ubuntu server.
    Install on Cloudron: Instructions on how to manually install Baserow on Cloudron.

## Development

Everything related to contributing and developing for Baserow.

    Development environment: Setting up your local development environment using docker-compose.
    Directory structure: The structure of all the directories in the Baserow repository explained.
    Tools: The tools (flake8, pytest, eslint, etc) and how to use them.
    Code quality: More information about the the code style, quality, choices we made, and how we enforce them.

## Plugins

Everything related to custom plugin development.

    Plugin basics: An introduction into Baserow plugins.
    Plugin boilerplate: Don’t reinvent the wheel, use the boilerplate for quick plugin development.
    Create application: Want to create an application type? Learn how to do that here.
    Create database table view: Display table data like a calendar, Kanban board or however you like by creating a view type.
    Create database table view filter: Filter the rows of a view with custom conditions.
    Create database table field: You can store data in a custom format by creating a field type.
    Creata a field converter: Converters alter a field and convert the related data for specific field changes.



## Accessing web dashboard

Open up the dashboard on http://localhost:8080/

You will be presented with the Sign-in screen. If you are on a freshly created instance, then you need to create a user first.

### First user

Use the dashboard to sign-up as the first user or call the sign-up API manually to create the first user. Users must create a password with at least 8 characters.


API CALL

As you will see later in [actions](/actions/actions.md) sign up and sign in api's are nothing special but just actions defined on certain tables.

Request 

```bash
curl 'http://localhost/action/user_account/signup' 
--data '{"attributes":{"name":"name","email":"email@domain.com","password":"password123","passwordConfirm":"password123"}}'
```

Response

```json
[{
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "Created user_account",
		"title": "Success",
		"type": "success"
	}
}, {
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "Created usergroup",
		"title": "Success",
		"type": "success"
	}
}, {
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "Created user_account_user_account_id_has_usergroup_usergroup_id",
		"title": "Success",
		"type": "success"
	}
}, {
	"ResponseType": "client.notify",
	"Attributes": {
		"__type": "client.notify",
		"message": "Sign-up successful. Redirecting to sign in",
		"title": "Success",
		"type": "success"
	}
}, {
	"ResponseType": "client.redirect",
	"Attributes": {
		"__type": "client.redirect",
		"delay": 2000,
		"location": "/auth/signin",
		"window": "self"
	}
}]
```

Nothing important in the response of signup to keep track of. 

Successful response means now we can login as a user and become the administrator.

A failure response would look like this:

```json
[{
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "Failed to create user_account. Error 1062: Duplicate entry 'email@domain.com' for key 'i79f4e12e72442d30f2b99a84fce3c392'",
		"title": "Failed",
		"type": "error"
	}
}]
```

Or 

```json
[{
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "http error (400) email and 0 more errors, invalid value for email",
		"title": "failed",
		"type": "error"
	}
}]
```


### Logging in dashboard


API CAll

Request

```bash
curl 'http://localhost/action/user_account/signin' 
--data '{"attributes":{"email":"email@domain.com","password":"password123"}}'
```

Response

```json
[{
	"ResponseType": "client.store.set",
	"Attributes": {
		"key": "token",
		"value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFydHBhckBnbWFpbC5jb20iLCJleHAiOjE1ODE2MTcxNTEsImlhdCI6IjIwMjAtMDItMTBUMjM6MzU6NTEuMTc2MjA5ODAxKzA1OjMwIiwiaXNzIjoiZGFwdGluLTNhZTI5ZCIsImp0aSI6IjQ4MTRkYjhhLTg1ZWEtNDc0ZS1iMWQ0LWQ5OGM4MTU5ZDU5MCIsIm5hbWUiOiJwYXJ0aCIsIm5iZiI6MTU4MTM1Nzk1MSwicGljdHVyZSI6Imh0dHBzOi8vd3d3LmdyYXZhdGFyLmNvbS9hdmF0YXIvM2M5MjI3NmI4NmMzNGJkNjZmZjQwMzFlNjNmM2JkZTdcdTAwMjZkPW1vbnN0ZXJpZCJ9.deocIlHXWH_2fsrYBx5lSGQVJxad044tj4j4amy2Zyk"
	}
}, {
	"ResponseType": "client.cookie.set",
	"Attributes": {
		"key": "token",
		"value": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFydHBhckBnbWFpbC5jb20iLCJleHAiOjE1ODE2MTcxNTEsImlhdCI6IjIwMjAtMDItMTBUMjM6MzU6NTEuMTc2MjA5ODAxKzA1OjMwIiwiaXNzIjoiZGFwdGluLTNhZTI5ZCIsImp0aSI6IjQ4MTRkYjhhLTg1ZWEtNDc0ZS1iMWQ0LWQ5OGM4MTU5ZDU5MCIsIm5hbWUiOiJwYXJ0aCIsIm5iZiI6MTU4MTM1Nzk1MSwicGljdHVyZSI6Imh0dHBzOi8vd3d3LmdyYXZhdGFyLmNvbS9hdmF0YXIvM2M5MjI3NmI4NmMzNGJkNjZmZjQwMzFlNjNmM2JkZTdcdTAwMjZkPW1vbnN0ZXJpZCJ9.deocIlHXWH_2fsrYBx5lSGQVJxad044tj4j4amy2Zyk"
	}
}, {
	"ResponseType": "client.notify",
	"Attributes": {
		"message": "Logged in",
		"title": "Success",
		"type": "success"
	}
}, {
	"ResponseType": "client.redirect",
	"Attributes": {
		"delay": 2000,
		"location": "/",
		"window": "self"
	}
}]
```

The token is to be used in the Authorization header of for all HTTP calls to identify the user.

## Become Administrator

First user to sign up with automatically become an administrator. More administrators can be added.


