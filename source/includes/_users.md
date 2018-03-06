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
type | integer | false | 0 (see <a href="#type">`type`</a>)
accessLevel | integer | false | 0 (see <a href="#access-level">`accessLevel`</a>)
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
    "accessLevel": 0,
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

## Retrieve all users

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

This endpoint retrieves all users. If the requesting user has an `accessLevel` of 0 (admin), all possible users will be returned. Else, the `currentFacility` query must be used and only users that are assigned to that facility will be returned.

### HTTP Request

`GET http://localhost/api/users`

### Query parameters

Parameter | Type | Description
--------- | ---- | -----------
type | int | Use for retrieving users of a specific type (0: Admin, 1: Instructor, 2: Participant)
currentFacility | string | If user is not an HZ admin, this is used to get users for the users's current facility context

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
    "accessLevel": 0,
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
    "accessLevel": 1,
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
type | integer | false | 0  (see <a href="#type">`type`</a>)
accessLevel | integer | false | 0 (see <a href="#access-level">`accessLevel`</a>)
masterAccount | string | false | null
deleted | boolean | false | false
facebookId | string | false | null
twitterId | string | false | null
googleId | string | false | null
passwordReset | boolean | false | false
picture | objectid | false | null (see <a href="#pictures">`Pictures`</a>)
address | Address | false | null (see <a href="#address">`address`</a>)
