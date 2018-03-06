# Participants

## Create a Participant

```shell
curl "http://localhost/api/participants"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6fc2077a27d66e90f53a03",
    "updatedAt": "2018-02-19T20:34:55.193Z",
    "createdBy": "5a8b33d24456d4ad1bd97546",
    "studentId": "51235",
    "nickName": "The Big Flame",
    "phone": "574-440-4159",
    "age": 30,
    "gender": 0,
    "weight": 160,
    "heightFeet": 6,
    "heightInches": 0,
    "walkingStride": 36,
    "runningStride": 60,
    "sensor": 72,
    "__v": 0,
    "address": {
        "createdAt": "2018-02-19T20:33:07.489Z"
    },
    "createdAt": "2018-02-19T20:33:07.489Z",
    "passwordReset": false,
    "deleted": false,
    "hasPortalAccess": false,
    "facilities": [
        "5a886c79e51643053974f74a"
    ],
    "lastName": "Dragon",
    "firstName": "Vicerus",
    "email": "participantTony@test.com",
    "classesAttended": 0,
    "lastClass": "None"
}
```

This endpoint creates a new participant. All properties in the model (participant.js) are allowed and may be included.

### HTTP Request

`POST http://localhost/api/participants`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
email | string | true |
firstName | string | true |
lastName | string | false |
currentFacility | objectid | true | The current facility context ID
phone | string | false |
nickName | string | false |
studentId | string | false | For internal school use
age | integer | false |
gender | integer | false |
weight | integer | false | Weight in lbs
heightFeet | integer | false |
heightInches | integer | false |
walkingStride | integer | false | Stride in inches
runningStride | integer | false | Stride in inches
sensor | integer | false | Sensor ID number
hasPortalAccess | boolean | false |
deleted | boolean | false | false
facebookId | string | false | null
twitterId | string | false | null
googleId | string | false | null
passwordReset | boolean | false | false
picture | objectid | false | null
address | Address | false | null (see <a href="#address">`address`</a>)


## Get a Specific Participant

```shell
curl "http://localhost/api/participants/5a6fc2077a27d66e90f53a03"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a6fc2077a27d66e90f53a03",
    "updatedAt": "2018-02-19T20:34:55.193Z",
    "createdBy": "5a8b33d24456d4ad1bd97546",
    "studentId": "51235",
    "nickName": "The Big Flame",
    "phone": "574-440-4159",
    "age": 30,
    "gender": 0,
    "weight": 160,
    "heightFeet": 6,
    "heightInches": 0,
    "walkingStride": 36,
    "runningStride": 60,
    "sensor": 72,
    "__v": 0,
    "address": {
        "createdAt": "2018-02-19T20:33:07.489Z"
    },
    "createdAt": "2018-02-19T20:33:07.489Z",
    "passwordReset": false,
    "deleted": false,
    "hasPortalAccess": false,
    "facilities": [
        "5a886c79e51643053974f74a"
    ],
    "lastName": "Dragon",
    "firstName": "Vicerus",
    "email": "participantTony@test.com",
    "classesAttended": 0,
    "lastClass": "None"
}
```

This endpoint takes the participant's id as a query paramater and returns the full participant object.

### HTTP Request

`GET http://localhost/api/participants/<id>`

## Get all Participants

```shell
curl "http://localhost/api/participants"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a72033e4bf51fa978b29036",
        "updatedAt": "2018-01-31T17:56:14.435Z",
        "createdBy": "5a6e27178b2fae714d17178a",
        "__v": 0,
        "address": {
            "createdAt": "2018-01-31T17:52:32.569Z"
        },
        "createdAt": "2018-01-31T17:52:32.569Z",
        "passwordReset": false,
        "deleted": false,
        "hasPortalAccess": false,
        "facilities": [
            "5a72027f4bf51fa978b29033"
        ],
        "lastName": "simons",
        "firstName": "Anthony",
        "email": "test@today2.com",
        "classedAttended": 0,
        "lastClass": "None"
    }
]
```

This endpoint takes the `currentFacility` id as a body parameter and returns all participants in that facility.

### HTTP Request

`GET http://localhost/api/participants`

## Delete a Participant

```shell
curl "http://localhost/api/participant/5a6fc2077a27d66e90f53a03"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "message": "Participant deleted successfully."
}
```

This endpoint takes the participant's id as a query parameter and returns `200` if successful.

### HTTP Request

`DELETE http://localhost/api/participant/<id>`

## Update a Participant

```shell
curl "http://localhost/api/participant/5a6fc2077a27d66e90f53a03"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "__v": 0,
    "updatedAt": "2018-01-30T00:53:27.721Z",
    "createdBy": "5a6e27178b2fae714d17178a",
    "_id": "5a6fc2077a27d66e90f53a03",
    "address": {
        "createdAt": "2018-01-30T00:51:59.419Z"
    },
    "createdAt": "2018-01-30T00:51:59.419Z",
    "passwordReset": false,
    "deleted": false,
    "hasPortalAccess": false,
    "lastName": "Daniels",
    "firstName": "Robert",
    "email": "test@today.com"
}
```

This endpoint takes the participant's id as a query paramater and returns the new participant object after saving.

### HTTP Request

`PUT http://localhost/api/participant/<id>`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
email | string | false |
firstName | string | false |
lastName | string | false |
currentFacility | objectid | true | The current facility context ID
phone | string | false |
nickName | string | false |
age | integer | false |
gender | integer | false |
weight | integer | false | Weight in lbs
heightFeet | integer | false |
heightInches | integer | false |
walkingStride | integer | false | Stride in inches
runningStride | integer | false | Stride in inches
sensor | integer | false | Sensor ID number
hasPortalAccess | boolean | false |
deleted | boolean | false | false
facebookId | string | false | null
twitterId | string | false | null
googleId | string | false | null
passwordReset | boolean | false | false
picture | objectid | false | null
address | Address | false | null (see <a href="#address">`address`</a>)
