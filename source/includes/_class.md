# Classes

## Create a class

```shell
curl "http://localhost/api/classes"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "__v": 0,
    "updatedAt": "2018-01-20T20:24:14.806Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z",
    "_id": "5a63a56efd397babebf06649",
    "createdAt": "2018-01-20T20:24:04.281Z",
    "deleted": false,
    "name": "new class name"
}
```

This endpoint creates a new class. All properties in the model (class.js) are allowed and may be included. You may also include an array of `Participant` objects to be created and added to the class along with this.

### HTTP Request

`POST http://localhost/api/classes`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | true |
date | date | true |
instructor | objectid | false |
participants | [objectid] | false |
description | string | false |
duration | integer | false | Duration in minutes
type | integer | false | Defaults to 0 when importing, and 1 when adding manually.
status | integer | false |

## Upload CSV File for Class

```shell
curl "http://localhost/api/classes/upload"
  -H "Authorization: Bearer {token}"
```

> The above command returns an empty response with statust `200` if the upload was succesful.

```json
```

This endpoint returns immediately once the file as completed uploading. The CSV parsing is done asynchronously and will alert the user via email once the parsing is complete or if there was an error during processing.

### HTTP Request

`POST http://localhost/api/classes/upload`

### Payload parameters

Parameter | Type
--------- | ----
classFile | form-data

## Retrieve all classes

```shell
curl "http://localhost/api/classes"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    {
        "_id": "5a63a56efd397babebf06649",
        "updatedAt": "2018-01-20T20:24:14.806Z",
        "createdBy": "5a6375a6e1986a50012351c8",
        "date": "2018-01-30T00:00:00.000Z",
        "__v": 0,
        "createdAt": "2018-01-20T20:24:04.281Z",
        "deleted": false,
        "name": "new class name"
    },
    {
        "_id": "5a63a5a5fd397babebf0664a",
        "updatedAt": "2018-01-20T20:25:09.248Z",
        "createdBy": "5a6375a6e1986a50012351c8",
        "date": "2018-01-30T00:00:00.000Z",
        "__v": 0,
        "createdAt": "2018-01-20T20:24:04.281Z",
        "deleted": false,
        "name": "new class name 2"
    }
]
```

This endpoint retrieves all classes if the user is an HZ admin. And only the classes the user is part of if accessLevel is `INSTRUCTOR` or `PARTICIPANT`

### HTTP Request

`GET http://localhost/api/classes`

### Query parameters

Parameter | Type | Description
--------- | ---- | -----------
limit | int | Limit the amount of classes returned
currentFacility | string | If user is not an HZ admin, this is used to get classes for the users's current facility context


## Get a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6faf7cb425a96c255122e7",
    "updatedAt": "2018-01-30T00:42:16.826Z",
    "createdBy": "5a6e27178b2fae714d17178a",
    "date": "2017-01-29T00:00:00.000Z",
    "__v": 3,
    "createdAt": "2018-01-29T23:33:30.445Z",
    "deleted": false,
    "participants": [
        {
            "_id": "5a6fb5979077386ceab252c8",
            "updatedAt": "2018-01-30T00:00:23.246Z",
            "createdBy": "5a6e27178b2fae714d17178a",
            "__v": 0,
            "address": {
                "createdAt": "2018-01-30T00:00:20.705Z"
            },
            "createdAt": "2018-01-30T00:00:20.705Z",
            "passwordReset": false,
            "deleted": false,
            "hasPortalAccess": false,
            "lastName": "Simons",
            "firstName": "Tony",
            "email": "test@test.com"
        }
    ],
    "instructor": "Todd Ramirez",
    "name": "Test class name"
}
```

This endpoint takes the class's id as a query paramater and returns the full class object.

### HTTP Request

`GET http://localhost/api/classes/<id>`

## Delete a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "message": "Class deleted successfully."
}
```

This endpoint takes the class's id as a query parameter and returns `200` if successful.

### HTTP Request

`DELETE http://localhost/api/classes/<id>`

## Update a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a63a56efd397babebf06649",
    "updatedAt": "2018-01-20T20:24:14.806Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z",
    "__v": 0,
    "createdAt": "2018-01-20T20:24:04.281Z",
    "deleted": false,
    "name": "updated class name"
}
```

This endpoint takes the class's id as a query paramater and returns the new class object after saving.

### HTTP Request

`PUT http://localhost/api/classes/<id>`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
date | date | false |
instructor | objectid | false |
participants | [objectid] | false |
description | string | false |
duration | integer | false | Duration in minutes
type | integer | false |
status | integer | false |


## Add a Participant to a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033/participants"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6faf7cb425a96c255122e7",
    "updatedAt": "2018-01-30T00:42:16.826Z",
    "createdBy": "5a6e27178b2fae714d17178a",
    "date": "2017-01-29T00:00:00.000Z",
    "__v": 3,
    "createdAt": "2018-01-29T23:33:30.445Z",
    "deleted": false,
    "participants": [
        {
            "_id": "5a6fb5979077386ceab252c8",
            "updatedAt": "2018-01-30T00:00:23.246Z",
            "createdBy": "5a6e27178b2fae714d17178a",
            "__v": 0,
            "address": {
                "createdAt": "2018-01-30T00:00:20.705Z"
            },
            "createdAt": "2018-01-30T00:00:20.705Z",
            "passwordReset": false,
            "deleted": false,
            "hasPortalAccess": false,
            "lastName": "Simons",
            "firstName": "Tony",
            "email": "test@test.com"
        }
    ],
    "instructor": "Todd Ramirez",
    "name": "Test class name"
}
```

This endpoint takes the class's id as a query paramater and returns the new class object after saving.

### HTTP Request

`POST http://localhost/api/classes/<id>/participants`

### Payload parameters

Parameter | Type
--------- | ----
participantId | string


## Remove a Participant from a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033/participants/5b2352f4bf51fa978b29279"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6faf7cb425a96c255122e7",
    "updatedAt": "2018-01-30T00:42:16.826Z",
    "createdBy": "5a6e27178b2fae714d17178a",
    "date": "2017-01-29T00:00:00.000Z",
    "__v": 3,
    "createdAt": "2018-01-29T23:33:30.445Z",
    "deleted": false,
    "participants": [],
    "instructor": "Todd Ramirez",
    "name": "Test class name"
}
```

This endpoint takes the class's id, and the participant's id as a query paramater and returns the new class object after saving.

### HTTP Request

`DELETE http://localhost/api/classes/<id>/participants/<participantId>`
