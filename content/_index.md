---
alwaysopen: true 
date: "2020-08-20T16:42:11.812Z"
description: Overview of daptin 

hide:
- toc 
post: "&nbsp;\U0001F44B"
title: Daptin 
weight: 2

---

Daptin is an open-source general purpose headless API server. You can use it for content management, workflow management, site management and so on.

Here is an introductory list of features

- User management
  - Extendable Sign up and Sign in API (1fa/2fa with password/TOTP)
  - Extensive authorization control table level/action level and row level
  - Rate limiting/connection throttling at IP/API level
- Data management
  - Declarative schema definition, relations and column properties
  - CRUD APIs with Authorization/Pagination/Search/Relations
  - File asset columns to store images/video/audio/blobs
- Storage/Asset management
  - localhost/gDrive/S3/B2/DropBox/FTP and many more supported
- Site management
  - Create HTTP sites based by storage anywhere
  - Enable HTTPS using LetsEncrypt
  - Create and Build HUGO static sites
  - Expose directories as FTP sites
- Integration and action management
  - Create workflows and expose as APIs
  - Call any 3rd party API by importing OpenAPI Spec
- Email management
  - Enable SMTPS and IMAPS services and use daptin as your regular email provider
  - Multi hostname mail server
  - Multiple email accounts
