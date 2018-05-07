# Users

## Register

```shell
curl "http://localhost/api/users/register"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1,
        "expiresAt": "2018-04-20T20:09:25.664Z"
    },
    "participantData": {
        "heartZones": {
            "shr": 80,
            "t1": 140,
            "t2": 170,
            "peak": 200
        },
        "hasPortalAccess": true,
        "metrics": []
    },
    "email": "tony7@thevalyreangroup.com",
    "firstName": "Tony Test",
    "lastName": "Simons",
    "facilities": [],
    "roles": [
        0
    ],
    "createdAt": "2018-03-30T20:09:20.303Z",
    "_id": "5abe99750717289239acb3b1",
    "lastLogin": "2018-03-30T20:09:25.663Z",
    "updatedAt": "2018-03-30T20:09:25.678Z"
}
```

This endpoint registers a new user and then automatically logs that instance in to the session. The user is registered with the `participant` role by default. An HZ admin must change this user's <a href="#roles">`ROLE`</a> if needed. The standard 21 day trial <a href="#license">`LICENSE`</a> is applied until changed by an HZ admin.

### HTTP Request

`POST http://localhost/api/users/register`

### Minimum Role Required

None

### Payload parameters

Parameter | Type | Required | Default
--------- | ---- | -------- | -------
email | string | true |
password | string | true | (Must be at least 8 characters and contain at least one digit)
firstName | string | true |
lastName | string | true |
nickName | string | false | null
phone | string | false | null
age | integer | false | null
gender | integer | false | null

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
    "license": {
        "status": 1,
        "expiresAt": "2018-04-20T20:09:25.664Z"
    },
    "participantData": {
        "heartZones": {
            "shr": 80,
            "t1": 140,
            "t2": 170,
            "peak": 200
        },
        "hasPortalAccess": true,
        "metrics": []
    },
    "email": "tony7@thevalyreangroup.com",
    "firstName": "Tony Test",
    "lastName": "Simons",
    "facilities": [],
    "roles": [
        0
    ],
    "createdAt": "2018-03-30T20:09:20.303Z",
    "_id": "5abe99750717289239acb3b1",
    "lastLogin": "2018-03-30T20:09:32.000Z",
    "updatedAt": "2018-03-30T20:09:32.940Z",
    "_token": "42ebc6a0-3456-11e8-ac2e-91b20e7db99e"
}
```

This endpoint authenticates the user with their credentials, logs them in to the session, and returns the user object. Use the `token` from this response as the user's bearer authorization.

### HTTP Request

`POST http://localhost/api/users/login`

### Minimum Role Required

None

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
        "license": {
            "status": 1
        },
        "email": "roger@test.com",
        "firstName": "Roger",
        "lastName": "Federer",
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "roles": [
            6
        ],
        "createdAt": "2018-03-31T17:54:24.756Z",
        "_id": "5abe96d3c8f7ba91c3870a47"
    },
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
        "email": "jamie@test.com",
        "firstName": "Jamie",
        "lastName": "Lannister",
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "roles": [
            0,
            1
        ],
        "createdAt": "2018-03-31T17:54:24.756Z",
        "_id": "5abe96d3c8f7ba91c3870a48"
    }
]
```

This endpoint retrieves all licensed users for use by internal admins

### HTTP Request

`GET http://localhost/api/users`

### Minimum Role Required

`SALES_SUPPORT`

## Retrieve all internal admin users

```shell
curl "http://localhost/api/users/all/internal"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "license": {
            "status": 1
        },
        "email": "roger@test.com",
        "firstName": "Roger",
        "lastName": "Federer",
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "roles": [
            6
        ],
        "createdAt": "2018-03-31T18:36:28.030Z",
        "_id": "5abfd52938cc8ca7ab6dd7ba"
    },
    {
        "license": {
            "status": 1
        },
        "email": "tony@thevalyreangroup.com",
        "firstName": "Tony",
        "lastName": "Simons",
        "facilities": [],
        "roles": [
            5
        ],
        "createdAt": "2018-03-31T18:36:28.030Z",
        "_id": "5abfd52938cc8ca7ab6dd7bd"
    },
    {
        "license": {
            "status": 1
        },
        "email": "bryan@iridiumsoftware.com",
        "firstName": "Bryan",
        "lastName": "Bellamy",
        "facilities": [],
        "roles": [
            4,
            3
        ],
        "createdAt": "2018-03-31T18:36:28.030Z",
        "_id": "5abfd52938cc8ca7ab6dd7be"
    }
]
```

This endpoint retrieves all internal admin users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users/all/internal`

### Minimum Role Required

`SUB_ADMIN`

## Retrieve all district admin users

```shell
curl "http://localhost/api/users/all/districtAdmins"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "license": {
            "status": 1
        },
        "email": "bryan@iridiumsoftware.com",
        "firstName": "Bryan",
        "lastName": "Bellamy",
        "facilities": [],
        "roles": [
            4,
            3
        ],
        "createdAt": "2018-03-31T18:39:31.678Z",
        "_id": "5abfd52938cc8ca7ab6dd7be"
    }
]
```

This endpoint retrieves all district admin users for use in the internal admin pages.

### HTTP Request

`GET http://localhost/api/users/all/districtAdmins`

### Minimum Role Required

`SALES_SUPPORT`

## Retrieve all facility admin users

```shell
curl "http://localhost/api/users/all/facilityAdmins"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "license": {
            "status": 1
        },
        "email": "kit@test.com",
        "firstName": "Kit",
        "lastName": "Harrington",
        "facilities": [],
        "roles": [
            2
        ],
        "createdAt": "2018-03-31T18:40:07.802Z",
        "_id": "5abfd52938cc8ca7ab6dd7bc",
        "totalLogins": 0
    }
]
```

This endpoint retrieves all district admin users for use in the internal/external admin pages.

### HTTP Request

`GET http://localhost/api/users/all/facilityAdmins`

### Minimum Role Required

`FACILITY_ADMIN`

## Retrieve all instructor users

```shell
curl "http://localhost/api/users/all/instructors"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
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
        "email": "jamie@test.com",
        "firstName": "Jamie",
        "lastName": "Lannister",
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "roles": [
            0,
            1
        ],
        "createdAt": "2018-03-31T18:44:33.303Z",
        "_id": "5abfd52938cc8ca7ab6dd7bb",
        "totalLogins": 0
    }
]
```

This endpoint retrieves all instructor users for use in the external admin pages. If a `currentFacility` query string is passed in with a facility id, only those users assigned to that facility will be returned.

### HTTP Request

`GET http://localhost/api/users/all/instructors`

### Minimum Role Required

`FACILITY_ADMIN`

## Retrieve all participant users

```shell
curl "http://localhost/api/users/all/participants"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "license": {
            "status": 1
        },
        "email": "jamie@test.com",
        "firstName": "Jamie",
        "lastName": "Lannister",
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "roles": [
            0,
            1
        ],
        "createdAt": "2018-03-31T20:40:44.037Z",
        "_id": "5abfea4870fbbfaa64994f66",
        "classesAttended": 0,
        "lastClass": "None"
    },
    {
        "license": {
            "status": 1
        },
        "email": "walter@white.com",
        "firstName": "Walter",
        "lastName": "White",
        "facilities": [],
        "roles": [
            0
        ],
        "createdAt": "2018-03-31T20:40:44.037Z",
        "_id": "5abfea4870fbbfaa64994f6a",
        "classesAttended": 0,
        "lastClass": "None"
    }
]
```

This endpoint retrieves all participant users for use in the external admin pages. If a `currentFacility` query string is passed in with a facility id, only those users assigned to that facility will be returned.

### HTTP Request

`GET http://localhost/api/users/all/participants`

### Minimum Role Required

`INSTRUCTOR`

## Get a Specific User

```shell
curl "http://localhost/api/users/5abfd52938cc8ca7ab6dd7bd"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1
    },
    "email": "tony@thevalyreangroup.com",
    "firstName": "Tony",
    "lastName": "Simons",
    "facilities": [],
    "roles": [
        5
    ],
    "createdAt": "2018-03-31T18:46:16.266Z",
    "_id": "5abfd52938cc8ca7ab6dd7bd"
}
```

This endpoint takes the user's id as a query parameter and returns the full user object.

### HTTP Request

`GET http://localhost/api/users/<id>`

### Minimum Role Required

NONE

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

### Minimum Role Required

`SALES_SUPPORT`

## Update a Specific User

```shell
curl "http://localhost/api/users/5abfd52938cc8ca7ab6dd7bd"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1
    },
    "email": "tony@thevalyreangroup.com",
    "firstName": "Tony",
    "lastName": "Simons",
    "facilities": [],
    "roles": [
        5
    ],
    "createdAt": "2018-03-31T18:53:13.493Z",
    "_id": "5abfd52938cc8ca7ab6dd7bd"
}
```

This endpoint takes the user's id as a query parameter and returns the new user object after saving.

### HTTP Request

`PUT http://localhost/api/users/<id>`

### Minimum Role Required

`SALES_SUPPORT` or must be called by the user being updated.

### Payload parameters

Parameter | Type | Required | Default
--------- | ---- | -------- | -------
email | string | false |
password | string | false |
firstName | string | false |
lastName | string | false |
nickName | string | false |
phone | string | false |
age | integer | false |
gender | integer | false |
role | [integer] | false | (see <a href="#roles">`ROLES`</a>)
license | integer | false | (see <a href="#license">`LICENSE`</a>)
address | Address | false | (see <a href="#address">`ADDRESS`</a>)

## Request a password reset

```shell
curl "http://localhost/api/users/5a72027f4bf51fa978b29033/requestReset"
```

> The above command returns JSON structured like this:

```json
{
    "message": "User pending password reset."
}
```

This endpoint takes the user's id as a query parameter, flags the user account for reset, and sends them an email with a link to `/passwordReset?resetToken=`

### HTTP Request

`POST http://localhost/api/users/<id>/requestReset`

### Minimum Role Required

NONE

## Process a password reset

```shell
curl "http://localhost/api/users/resetPassword"
```

> The above command returns JSON structured like this:

```json
{
    "license": {
        "status": 1
    },
    "email": "tony@thevalyreangroup.com",
    "firstName": "Tony",
    "lastName": "Simons",
    "facilities": [],
    "roles": [
        5
    ],
    "createdAt": "2018-03-31T18:53:13.493Z",
    "_id": "5abfd52938cc8ca7ab6dd7bd"
}
```

This endpoint takes the user's password `resetToken` and the new password as body paramaters.

### HTTP Request

`POST http://localhost/api/users/<id>/requestReset`

### Minimum Role Required

NONE

### Payload parameters

Parameter | Type | Required
--------- | ---- | --------
resetToken | String | true
password | String | true
