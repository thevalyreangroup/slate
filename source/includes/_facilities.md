# Facilities

## Create a Facility

```shell
curl "http://localhost/api/facilities"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "test facility 1",
    "type": 0,
    "createdAt": "2018-02-13T17:50:03.778Z",
    "_id": "5abfde10337566a8b385db17",
    "updatedAt": "2018-02-13T18:01:35.815Z",
    "createdBy": "5a75ee8b4b8d5fd5797d0863"
}
```

This endpoint creates a new facility.

### HTTP Request

`POST http://localhost/api/facilities`

### Minimum Role Required

`DISTRICT_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | true |
type | integer | false | (see <a href="#facility-type">`facility-type`</a>)
phone | string | false |
website | string | false |
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
    "createdAt": "2018-02-13T17:50:03.778Z",
    "type": 0,
    "name": "test name"
}
```

This endpoint takes the facility's id as a query parameter and returns the full facility object.

### HTTP Request

`GET http://localhost/api/facilities/<id>`

### Minimum Role Required

NONE

## Get all Facilities

```shell
curl "http://localhost/api/facilities"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "name": "test facility 1",
        "type": 0,
        "createdAt": "2018-02-13T17:50:03.778Z",
        "_id": "5abfdeab21aa27a8d32edb8a",
        "updatedAt": "2018-02-13T18:01:35.815Z",
        "createdBy": "5a75ee8b4b8d5fd5797d0863"
    },
    {
        "name": "test facility 2",
        "type": 0,
        "createdAt": "2018-02-13T17:50:03.778Z",
        "_id": "5abfdeab21aa27a8d32edb8b",
        "updatedAt": "2018-02-13T18:01:35.815Z",
        "createdBy": "5a75ee8b4b8d5fd5797d0863"
    }
]
```

This endpoint returns all facilities.

### HTTP Request

`GET http://localhost/api/facilities`

### Minimum Role Required

`DISTRICT_ADMIN`

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

### Minimum Role Required

`DISTRICT_ADMIN`

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
    "createdAt": "2018-02-13T17:50:03.778Z",
    "deleted": false,
    "type": 0,
    "name": "test name"
}
```

This endpoint takes the facility's id as a query paramater and returns the new facility object after saving.

### HTTP Request

`PUT http://localhost/api/facilities/<id>`

### Minimum Role Required

`FACILITY_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
type | integer | false | (see <a href="#facility-type">`facility-type`</a>)
phone | string | false |
website | string | false |
address | Address | false | null (see <a href="#address">`address`</a>)

## Add new user to Facility

```shell
curl "http://localhost/api/facilities/5abfdeab21aa27a8d32edb8a/users"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1
    },
    "email": "tony19@thevalyreangroup.com",
    "firstName": "tony test",
    "lastName": "simons test",
    "facilities": [
        "5abfdeab21aa27a8d32edb8a"
    ],
    "roles": [
        1
    ],
    "createdAt": "2018-03-31T19:23:23.217Z",
    "_id": "5abfe0381da7d2a8f0fe9d34",
    "createdBy": "5abfdeac21aa27a8d32edb94",
    "updatedAt": "2018-03-31T19:23:36.384Z"
}
```

This endpoint takes the facilities's id as a query parameter, creates a new user with the `instructor` role and returns the new participant object after saving. The new participant is notified via email with a temporary password.

### HTTP Request

`POST http://localhost/api/facilities/<id>/users`

### Minimum Role Required

`FACILITY_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
email | string | true |
firstName | string | true |
lastName | string | true |
nickName | string | false | null
phone | string | false | null
age | integer | false | null
gender | integer | false | null


## Add existing user to Facility

```shell
curl "http://localhost/api/facilities/5abfdeab21aa27a8d32edb8a/users"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1
    },
    "email": "walter@white.com",
    "firstName": "Walter",
    "lastName": "White",
    "facilities": [
        "5abfdeab21aa27a8d32edb8a",
    ],
    "roles": [
        0
    ],
    "createdAt": "2018-03-31T19:40:02.871Z",
    "_id": "5abfdeac21aa27a8d32edb99",
    "updatedAt": "2018-03-31T19:46:16.589Z",
    "updatedBy": "5abfdeac21aa27a8d32edb94"
}
```

This endpoint takes the facilities's id as a query parameter and adds an existing user to the participants list. The user must have the `participant` role and not already be attached to this facility.

### HTTP Request

`PUT http://localhost/api/facilities/<id>/users`

### Minimum Role Required

`FACILITY_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
userId | string | true | The existing user's id
