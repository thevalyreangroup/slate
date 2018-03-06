# Facilities

## Create

```shell
curl "http://localhost/api/facilities"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "__v": 0,
    "updatedAt": "2018-02-13T18:01:35.815Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "_id": "5a8327ffb2cc252d4bbb7d0b",
    "address": {
        "createdAt": "2018-02-13T17:50:03.778Z"
    },
    "createdAt": "2018-02-13T17:50:03.778Z",
    "deleted": false,
    "type": 0,
    "name": "test name"
}
```

This endpoint creates a new facility. All properties in the model (facility.js) are allowed and may be included.

### HTTP Request

`POST http://localhost/api/facilities`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | true |
type | integer | false | (see <a href="#facility-type">`address`</a>)
phone | string | false |
website | string | false |
picture | objectid | false | (see <a href="#pictures">`Pictures`</a>)
address | Address | false | null (see <a href="#address">`address`</a>)


## Get a Specific Facility

```shell
curl "http://localhost/api/facilities/5a8327ffb2cc252d4bbb7d0b"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a8327ffb2cc252d4bbb7d0b",
    "updatedAt": "2018-02-13T18:01:35.815Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "__v": 0,
    "address": {
        "createdAt": "2018-02-13T17:50:03.778Z"
    },
    "createdAt": "2018-02-13T17:50:03.778Z",
    "deleted": false,
    "type": 0,
    "name": "test name"
}
```

This endpoint takes the facility's id as a query paramater and returns the full facility object.

### HTTP Request

`GET http://localhost/api/facilities/<id>`

## Get all Facilities

```shell
curl "http://localhost/api/facilities"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "5a8327ffb2cc252d4bbb7d0b",
    "updatedAt": "2018-02-13T18:01:35.815Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "__v": 0,
    "address": {
        "createdAt": "2018-02-13T17:50:03.778Z"
    },
    "createdAt": "2018-02-13T17:50:03.778Z",
    "deleted": false,
    "type": 0,
    "name": "test name"
  }
]
```

This endpoint takes the facility's id as a query paramater and returns the full facility object.

### HTTP Request

`GET http://localhost/api/facilities`

## Delete a Facility

```shell
curl "http://localhost/api/facilities/5a8327ffb2cc252d4bbb7d0b"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "message": "Facility deleted successfully."
}
```

This endpoint takes the facility's id as a query parameter and returns `200` if successful.

### HTTP Request

`DELETE http://localhost/api/facilities/<id>`

## Update a Facility

```shell
curl "http://localhost/api/facilities/5a8327ffb2cc252d4bbb7d0b"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a8327ffb2cc252d4bbb7d0b",
    "updatedAt": "2018-02-13T18:01:35.815Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "__v": 0,
    "address": {
        "createdAt": "2018-02-13T17:50:03.778Z"
    },
    "createdAt": "2018-02-13T17:50:03.778Z",
    "deleted": false,
    "type": 0,
    "name": "test name"
}
```

This endpoint takes the facility's id as a query paramater and returns the new facility object after saving.

### HTTP Request

`PUT http://localhost/api/facilities/<id>`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
type | integer | false | (see <a href="#facility-type">`address`</a>)
phone | string | false |
website | string | false |
picture | objectid | false | (see <a href="#pictures">`Pictures`</a>)
address | Address | false | null (see <a href="#address">`address`</a>)

## Add new user to Facility

```shell
curl "http://localhost/api/facilities/5a8327ffb2cc252d4bbb7d0b/users"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "__v": 0,
    "updatedAt": "2018-02-13T18:10:07.296Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "hashedPassword": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6IjNwb2NKZzkifQ.tNVWdMZvCI5Xhu4w8fBpf8E0euB2eABkYZefD8TR8oQ",
    "_id": "5a8329ffb2cc252d4bbb7d0c",
    "address": {
        "createdAt": "2018-02-13T17:50:03.802Z"
    },
    "logs": [],
    "createdAt": "2018-02-13T17:50:03.802Z",
    "passwordReset": true,
    "deleted": false,
    "accessLevel": 6,
    "type": 2,
    "facilities": [
        "5a8327ffb2cc252d4bbb7d0b"
    ],
    "lastName": "simons",
    "firstName": "test 234",
    "email": "tony234@thevalyreangroup.com"
}
```

This endpoint takes the facilities's id as a query paramater, creates a new user with the `participant` type and returns the new participant object after saving. The new participant is notified via email with a temporary password,

### HTTP Request

`POST http://localhost/api/facilities/<id>/users`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
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


## Add existing user to Facility

```shell
curl "http://localhost/api/facilities/5a8327ffb2cc252d4bbb7d0b/users"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a8329ffb2cc252d4bbb7d0c",
    "updatedAt": "2018-02-13T18:14:19.000Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863",
    "hashedPassword": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXNzd29yZCI6IjNwb2NKZzkifQ.tNVWdMZvCI5Xhu4w8fBpf8E0euB2eABkYZefD8TR8oQ",
    "__v": 0,
    "updatedBy": "5a75ee8b4b8d5fd5797d0863",
    "address": {
        "createdAt": "2018-02-13T17:50:03.802Z"
    },
    "logs": [],
    "createdAt": "2018-02-13T17:50:03.802Z",
    "passwordReset": true,
    "deleted": false,
    "accessLevel": 6,
    "type": 2,
    "facilities": [
        "5a8327ffb2cc252d4bbb7d0b",
        "5a23vehfb2cc2wefv2537d06"
    ],
    "lastName": "simons",
    "firstName": "test 234",
    "email": "tony234@thevalyreangroup.com"
}
```

This endpoint takes the facilities's id as a query paramater and adds an existing user to the participants list. The user must be of `type` participant.

### HTTP Request

`PUT http://localhost/api/facilities/<id>/users`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
userId | string | true | The existing user's id
