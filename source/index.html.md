---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='http://heartzones-dev.us-east-1.elasticbeanstalk.com/'>Project Site</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - users
  - class
  - participants
  - media
  - facilities
  - pictures
  - errors
  - enums
  - classes

search: true
---

# Introduction

Welcome to the HeartZones API!

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "/api/user"
  -H "Authorization: Bearer {token}"
```

HeartZones uses API JWT tokens to allow access to the API.

The API expects for the token to be included in all authenticated API requests to the server in a header that looks like the following:

`Authorization: Bearer {token}`

<aside class="notice">
You must replace <code>token</code> with user's JWT token.
</aside>
