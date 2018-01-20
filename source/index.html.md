---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='http://heartzones-dev.us-east-1.elasticbeanstalk.com/'>Project Site</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

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

`Authorization: Bearer {token}}`

<aside class="notice">
You must replace <code>token</code> with user's JWT token.
</aside>

# Users

## Register

```shell
curl "http://localost/api/users/register"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6375a6e1986a50012351c8",
    "updatedAt": "2018-01-20T17:00:22.642Z",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
    "__v": 0,
    "address": {
        "createdAt": "2018-01-20T17:00:17.383Z"
    },
    "createdAt": "2018-01-20T17:00:17.383Z",
    "passwordReset": false,
    "deleted": false,
    "accessLevel": 0,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup.com"
}
```

This endpoint registers a new user and then automatically logs that instance in to the session. All properties in the model (user.js) are allowed and may be included.

### HTTP Request

`POST http://localhost/api/users/register`

### Payload parameters

Parameter | Required
--------- | --------
email | true
password | true
firstName | true
lastName | true

<aside class="success">
We do not store passwords. They are hashed and returned as a JWT.
</aside>


## Retrieve all users

```shell
curl "http://localost/api/users"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a6375a6e1986a50012351c8",
        "updatedAt": "2018-01-20T17:00:22.642Z",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-20T17:00:17.383Z"
        },
        "createdAt": "2018-01-20T17:00:17.383Z",
        "passwordReset": false,
        "deleted": false,
        "accessLevel": 0,
        "type": 0,
        "lastName": "simons",
        "firstName": "tony",
        "email": "tony@thevalyreangroup4.com"
    },
    {
        "_id": "5a6375a6e1986a50012351c8",
        "updatedAt": "2018-01-20T17:00:22.642Z",
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-20T17:00:17.383Z"
        },
        "createdAt": "2018-01-20T17:00:17.383Z",
        "passwordReset": false,
        "deleted": false,
        "accessLevel": 0,
        "type": 0,
        "lastName": "simons",
        "firstName": "tony",
        "email": "tony@thevalyreangroup5.com"
    }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET http://example.com/api/users`


## Get a Specific User

```shell
curl "http://localost/api/users/v"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6375a6e1986a50012351c8",
    "updatedAt": "2018-01-20T17:00:22.642Z",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
    "__v": 0,
    "address": {
        "createdAt": "2018-01-20T17:00:17.383Z"
    },
    "createdAt": "2018-01-20T17:00:17.383Z",
    "passwordReset": false,
    "deleted": false,
    "accessLevel": 0,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup.com"
}
```

This endpoint takes the user's id as a query paramater and returns the full user object.

### HTTP Request

`GET http://localhost/api/users/<id>`

## Delete a Specific User

```shell
curl "http://localost/api/users/<id>"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "message": "User deleted successfully."
}
```

This endpoint takes the user's id as a query parameter and returns `200` if successful.

### HTTP Request

`DELETE http://localhost/api/users/<id>`

## Update a Specific User

```shell
curl "http://localost/api/users/<id>"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6375a6e1986a50012351c8",
    "updatedAt": "2018-01-20T17:00:22.642Z",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
    "__v": 0,
    "address": {
        "createdAt": "2018-01-20T17:00:17.383Z"
    },
    "createdAt": "2018-01-20T17:00:17.383Z",
    "passwordReset": false,
    "deleted": false,
    "accessLevel": 1,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup.com"
}
```

This endpoint takes the user's id as a query paramater and returns the new user object after saving.

### HTTP Request

`PUT http://localhost/api/users/<id>`

### Payload parameters

Parameter | Type
--------- | ---- 
accessLevel | true
