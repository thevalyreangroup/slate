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
    "name": "new class name"
}
```

This endpoint creates a new class. You may also include an array of `Participant` id's to be created and added to the class along with this.

### HTTP Request

`POST http://localhost/api/classes`

### Minimum Role Required

`INSTRUCTOR`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | true |
date | date | true |
instructor | string | true |
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

> The above command returns an empty response with status `200` if the upload was successful.

```json
```

This endpoint returns immediately once the file as completed uploading. The CSV parsing is done asynchronously and will alert the user via email once the parsing is complete or if there was an error during processing.

### HTTP Request

`POST http://localhost/api/classes/upload`

### Minimum Role Required

`INSTRUCTOR`

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
[
    {
        "name": "Test class name 1",
        "instructor": "Kate Austin",
        "participants": [],
        "createdAt": "2018-01-20T20:24:04.281Z",
        "_id": "5abfea4770fbbfaa64994f56",
        "__v": 0,
        "updatedAt": "2018-01-20T20:24:14.806Z",
        "createdBy": "5a6375a6e1986a50012351c8",
        "date": "2018-01-30T00:00:00.000Z"
    },
    {
        "name": "Test class name 2",
        "instructor": "Jack Shepherd",
        "participants": [],
        "createdAt": "2018-01-20T20:24:04.281Z",
        "_id": "5abfea4770fbbfaa64994f57",
        "__v": 0,
        "updatedAt": "2018-01-20T20:24:14.806Z",
        "createdBy": "5a6375a6e1986a50012351c8",
        "date": "2018-01-30T00:00:00.000Z"
    }
]
```

This endpoint retrieves all non-deleted classes based on the following conditions:  
  
---Returns all classes this participant is a part of---  
-User has only one role and is a `participant`.  
-User has multiple roles with one including `participant` and the query string `asParticipant` is included.  

---Returns all classes this instructor is a part of---  
-User has only one role and is an `instructor`.  
-User has multiple roles with one including `instructor` and the query string `asInstructor` is included.  

---Returns all classes---  
-None of the above conditions were met.  

### HTTP Request

`GET http://localhost/api/classes`

### Minimum Role Required

NONE

### Query parameters

Parameter | Type | Description
--------- | ---- | -----------
limit | int | Limit the amount of classes returned


## Get a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "Test class name 1",
    "instructor": "Kate Austin",
    "participants": [
        {
            "license": {
                "status": 1
            },
            "participantData": {
                "heartZones": {
                    "shr": 80,
                    "t1": 140,
                    "t2": 170,
                    "peak": 200
                },
                "hasPortalAccess": true,
                "metrics": [],
                "studentId": 3023,
                "weight": 160,
                "heightInches": 96,
                "walkingStride": 36,
                "runningStride": 72,
                "birthdate": "2018-09-28T00:00:00.000Z"
            },
            "email": "walter@white.com",
            "firstName": "Walter",
            "lastName": "White",
            "facilities": [],
            "roles": [
                0
            ],
            "createdAt": "2018-03-31T20:27:22.530Z",
            "_id": "5abfea4870fbbfaa64994f6a"
        }
    ],
    "createdAt": "2018-01-20T20:24:04.281Z",
    "_id": "5abfea4770fbbfaa64994f56",
    "updatedAt": "2018-03-31T20:27:23.000Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z"
}
```

This endpoint takes the class's id as a query parameter and returns the full class object with all participants and their respective data.

### HTTP Request

`GET http://localhost/api/classes/<id>`

### Minimum Role Required

NONE

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

### Minimum Role Required

`INSTRUCTOR`

## Update a Specific Class

```shell
curl "http://localhost/api/classes/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "Test class name 4",
    "instructor": "Roger Bloomingdale",
    "participants": [],
    "createdAt": "2018-01-20T20:24:04.281Z",
    "_id": "5abfea4770fbbfaa64994f56",
    "updatedAt": "2018-01-20T20:24:14.806Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z"
}
```

This endpoint takes the class's id as a query parameter and returns the new class object after saving.

### HTTP Request

`PUT http://localhost/api/classes/<id>`

### Minimum Role Required

`INSTRUCTOR`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
date | date | false |
instructor | string | false |
participants | [objectid] | false |
description | string | false |
duration | integer | false | Duration in minutes
type | integer | false |
status | integer | false |


## Add a Participant to a Specific Class

```shell
curl "http://localhost/api/classes/5abfea4770fbbfaa64994f56/participants"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "Test class name 1",
    "instructor": "Kate Austin",
    "participants": [
        {
            "license": {
                "status": 1
            },
            "participantData": {
                "heartZones": {
                    "shr": 80,
                    "t1": 140,
                    "t2": 170,
                    "peak": 200
                },
                "hasPortalAccess": true,
                "metrics": [],
                "studentId": 3023,
                "weight": 160,
                "heightInches": 96,
                "walkingStride": 36,
                "runningStride": 72,
                "birthdate": "2018-09-28T00:00:00.000Z"
            },
            "email": "walter@white.com",
            "firstName": "Walter",
            "lastName": "White",
            "facilities": [],
            "roles": [
                0
            ],
            "createdAt": "2018-03-31T20:27:22.530Z",
            "_id": "5abfea4870fbbfaa64994f6a"
        }
    ],
    "createdAt": "2018-01-20T20:24:04.281Z",
    "_id": "5abfea4770fbbfaa64994f56",
    "updatedAt": "2018-03-31T20:27:23.000Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z"
}
```

This endpoint takes the class's id as a query parameter and returns the new class object after saving.

### HTTP Request

`POST http://localhost/api/classes/<id>/participants`

### Minimum Role Required

`INSTRUCTOR`

### Payload parameters

Parameter | Type
--------- | ----
userId | string


## Remove a Participant from a Specific Class

```shell
curl "http://localhost/api/classes/5abfea4770fbbfaa64994f56/participants/5abfea4870fbbfaa64994f6a"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "Test class name 1",
    "instructor": "Kate Austin",
    "participants": [],
    "createdAt": "2018-01-20T20:24:04.281Z",
    "_id": "5abfea4770fbbfaa64994f56",
    "updatedAt": "2018-03-31T20:27:23.000Z",
    "createdBy": "5a6375a6e1986a50012351c8",
    "date": "2018-01-30T00:00:00.000Z"
}
```

This endpoint takes the class's id, and the participant's id as a query parameter and returns the new class object after saving.

### HTTP Request

`DELETE http://localhost/api/classes/<id>/participants/<participantId>`

### Minimum Role Required

`INSTRUCTOR`
