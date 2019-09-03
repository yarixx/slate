---
title: SAYMON Server REST API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - authentication
  - kittens
  - errors
  - template

search: true
---

# Introduction

Welcome to the SAYMON API! You can use our API to access SAYMON API endpoints, which can get information on objects in our database.

We have language bindings in Shell, Python and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/lord/slate).

# General information

This documentation provides description of all SAYMON REST API methods.

Each method description contains:

* method verb (`GET`, `POST` etc.);
* method URL (like `/node/api/users/session`);
* short method description;
* required permissions specification (if method requires permissions);
* method parameters specification (if method has parameters);
* method options specification (if method has options);
* request body example (if method expects body);
* response example (if method returns non-empty response body).

## Method URL

Method URl is relative to your actual SAYMON installation host name. You get the full method URL by appending method URL in description to your SAYMON host name URL. Example:

`https://saas.saymon.info` + `/node/api/users/session` = `https://saas.saymon.info/node/api/users/session`

## Method permissions

If a method requires specific permissions from a user, these permissions are listed in `Permissions` section.

For example, method `POST /node/api/agents/update` specifies `upload-agent-updates` as a required permission. This means that a user that executes this method should have this permission.

Some methods may specify `objectPermissions` or `linkPermissions`. This means that a method will successfully execute only if a user has access to a specific Object or Link respectively.

Permissions can be combined. Example: `objectPermissions + (create-objects | manage-objects)` - means that a user, who's executing a request, should have access to an object, on which the method is being executed, AND should have `create-objects` OR `manage-objects` permission additionally.

## Method parameters

Method parameters are those method URL segments enclosed in brackets (`{}`). These segments are replaced with actual values when you form a request.

Let's say we want to use `/node/api/classes/{id}/object-count` method with parameter `id=24`. We will get:

`/node/api/classes/{id}/object-count` -> `/node/api/classes/24/object-count`

## Method options

Method options are additional inputs to REST method, that can be added after question sign (`?`) using URL parameter format.

For example, if we want to use `/node/api/objects/{id}/history` with parameter `id=333` and options `from=3m-ago` and `to=1m-ago`, we will get:

`/node/api/objects/{id}/history` -> `/node/api/objects/333/history` -> `/node/api/objects/333/history?from=3m-ago&to=1m-ago`
