# Users

## Register

```shell
curl "http://localhost/api/users/register"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6375a6e1986a50012351c8",
    "updatedAt": "2018-01-20T17:00:22.642Z",
    "token": "23113cd0-1015-11e8-8571-b59c57efe38a",
    "__v": 0,
    "address": {
        "createdAt": "2018-01-20T17:00:17.383Z"
    },
    "createdAt": "2018-01-20T17:00:17.383Z",
    "passwordReset": false,
    "deleted": false,
    "type": 0,
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

Parameter | Type | Required | Default
--------- | ---- | -------- | -------
email | string | true |
password | string | true |
firstName | string | true |
lastName | string | true |
nickName | string | false | null
facilities | [objectid] | false | null
phone | string | false | null
age | integer | false | null
gender | integer | false | null
type | integer | false | 0 (see <a href="#account-type">`type`</a>)
license | integer | false | 1 (see <a href="#license">`license`</a>)
masterAccount | string | false | null
deleted | boolean | false | false
facebookId | string | false | null
twitterId | string | false | null
googleId | string | false | null
passwordReset | boolean | false | false
picture | objectid | false | null (see <a href="#pictures">`Pictures`</a>)
address | Address | false | null (see <a href="#address">`address`</a>)

<aside class="success">
We do not store plain-text passwords, they are all hashed.
</aside>

## Login

```shell
curl "http://localhost/api/users/login"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6375a6e1986a50012351c8",
    "updatedAt": "2018-01-20T17:00:22.642Z",
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6InRlc3RpbmcifQ.1Zu7P_364ymSQGUaRR0bMD_NtfGSh0WNT5qV0UxXz-Q",
    "__v": 0,
    "lastLogin": "2018-01-20T20:59:06.000Z",
    "address": {
        "createdAt": "2018-01-20T17:00:17.383Z"
    },
    "createdAt": "2018-01-20T17:00:17.383Z",
    "passwordReset": false,
    "deleted": false,
    "type": 0,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup4.com"
}
```

This endpoint authenticates the user with their credentials, logs them in to the session, and returns the user object.

### HTTP Request

`POST http://localhost/api/users/login`

### Payload parameters

Parameter | Required
--------- | --------
email | true
password | true

## Retrieve all licensed users

```shell
curl "http://localhost/api/users"
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
        "type": 0,
        "license": 1,
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
        "type": 0,
        "license": 1,
        "lastName": "simons",
        "firstName": "tony",
        "email": "tony@thevalyreangroup5.com"
    }
]
```

This endpoint retrieves all licensed users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users`

## Retrieve all district admin users

```shell
curl "http://localhost/api/users/all/districtAdmins"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18cb",
        "updatedAt": "2018-01-20T17:00:22.642Z",
        "token": "23113cd0-1015-11e8-8571-b59c57efe38a",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-20T17:00:17.383Z"
        },
        "logs": [],
        "createdAt": "2018-01-20T17:00:17.383Z",
        "passwordReset": false,
        "deleted": false,
        "license": 1,
        "type": 3,
        "facilities": [],
        "lastName": "Harrington",
        "firstName": "Kit",
        "email": "kit@test.com"
    }
]
```

This endpoint retrieves all district admin users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users/all/districtAdmins`

## Retrieve all facility admin users

```shell
curl "http://localhost/api/users/all/facilityAdmins"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18cd",
        "updatedAt": "2018-01-20T17:00:22.642Z",
        "token": "23113cd0-1015-11e8-8571-b59c57efe38a",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-20T17:00:17.383Z"
        },
        "createdAt": "2018-01-20T17:00:17.383Z",
        "passwordReset": false,
        "deleted": false,
        "license": 1,
        "type": 4,
        "facilities": [],
        "lastName": "Bellamy",
        "firstName": "Bryan",
        "email": "bryan@iridiumsoftware.com",
        "totalLogins": 0
    }
]
```

This endpoint retrieves all district admin users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users/all/facilityAdmins`

## Retrieve all instructor users

```shell
curl "http://localhost/api/users/all/instructors"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18cc",
        "updatedAt": "2018-01-20T17:00:22.642Z",
        "token": "23113cd0-1015-11e8-8571-b59c57efe38a",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-20T17:00:17.383Z"
        },
        "createdAt": "2018-01-20T17:00:17.383Z",
        "passwordReset": false,
        "deleted": false,
        "license": 1,
        "type": 5,
        "facilities": [],
        "lastName": "Simons",
        "firstName": "Tony",
        "email": "tony@thevalyreangroup.com",
        "totalLogins": 0
    }
]
```

This endpoint retrieves all district admin users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users/all/facilityAdmins`

## Get a Specific User

```shell
curl "http://localhost/api/users/5a72027f4bf51fa978b29033"
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
    "type": 0,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup.com"
}
```

This endpoint takes the user's id as a query parameter and returns the full user object.

### HTTP Request

`GET http://localhost/api/users/<id>`

## Delete a Specific User

```shell
curl "http://localhost/api/users/5a72027f4bf51fa978b29033"
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
curl "http://localhost/api/users/5a72027f4bf51fa978b29033"
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
    "type": 1,
    "type": 0,
    "lastName": "simons",
    "firstName": "tony",
    "email": "tony@thevalyreangroup.com"
}
```

This endpoint takes the user's id as a query parameter and returns the new user object after saving.

### HTTP Request

`PUT http://localhost/api/users/<id>`

### Payload parameters

Parameter | Type
--------- | ----
Parameter | Type | Required | Default
--------- | ---- | -------- | -------
email | string | false |
password | string | false |
firstName | string | false |
lastName | string | false |
nickName | string | false | null
facilities | [objectid] | false | null
phone | string | false | null
age | integer | false | null
gender | integer | false | null
type | integer | false | 0 (see <a href="#account-type">`type`</a>)
license | integer | false | 1 (see <a href="#license">`license`</a>)
masterAccount | string | false | null
deleted | boolean | false | false
facebookId | string | false | null
twitterId | string | false | null
googleId | string | false | null
passwordReset | boolean | false | false
picture | objectid | false | null (see <a href="#pictures">`Pictures`</a>)
address | Address | false | null (see <a href="#address">`address`</a>)
