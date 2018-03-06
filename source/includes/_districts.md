# Districts

## Create

```shell
curl "http://localhost/api/districts"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "__v": 0,
    "updatedAt": "2018-03-06T17:19:53.186Z",
    "createdBy": "5a9ec0c3ee8b0bfb4ffc18c9",
    "_id": "5a9ecdb91f8ab6fc6caf0ff7",
    "createdAt": "2018-03-06T16:44:24.861Z",
    "deleted": false,
    "facilities": [],
    "identifier": "54372",
    "name": "District 7"
}
```

This endpoint creates a new district. All properties in the model (district.js) are allowed and may be included.

### HTTP Request

`POST http://localhost/api/districts`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
admin | objectid | false | The district admin <a href="#users">`User`</a>)
name | string | true | (see <a href="#facility-type">`address`</a>)
identifier | string | true |


## Get all Districts

```shell
curl "http://localhost/api/districts"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18c4",
        "__v": 0,
        "updatedAt": "2018-03-06T16:28:31.000Z",
        "createdBy": "5a8b33d24456d4ad1bd97546",
        "updatedBy": "5a9ec0c3ee8b0bfb4ffc18c9",
        "createdAt": "2018-03-06T16:15:20.651Z",
        "deleted": false,
        "facilities": [],
        "identifier": "5437",
        "name": "District 1"
    },
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18c5",
        "__v": 0,
        "updatedAt": "2018-03-06T16:15:22.756Z",
        "createdBy": "5a8b33d24456d4ad1bd97546",
        "createdAt": "2018-03-06T16:15:20.651Z",
        "deleted": false,
        "facilities": [],
        "identifier": "344347",
        "name": "District 2"
    }
]
```

This endpoint returns all districts registered

### HTTP Request

`GET http://localhost/api/districts`

## Delete a District

```shell
curl "http://localhost/api/districts/5a9ec0c3ee8b0bfb4ffc18c5"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "message": "District deleted successfully."
}
```

This endpoint takes the districts's id as a query parameter and returns `200` if successful.

### HTTP Request

`DELETE http://localhost/api/districts/<id>`

## Update a District

```shell
curl "http://localhost/api/districts/5a9ec0c3ee8b0bfb4ffc18c5"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a9ec0c3ee8b0bfb4ffc18c4",
    "__v": 0,
    "updatedAt": "2018-03-06T16:28:31.000Z",
    "createdBy": "5a8b33d24456d4ad1bd97546",
    "updatedBy": "5a9ec0c3ee8b0bfb4ffc18c9",
    "createdAt": "2018-03-06T16:15:20.651Z",
    "deleted": false,
    "facilities": [],
    "identifier": "5437",
    "name": "District 1"
}
```

This endpoint takes the districts's id as a query paramater and returns the new participant object after saving.

### HTTP Request

`PUT http://localhost/api/facilities/<id>`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
identifier | integer | false |

## Add existing Facility to District

```shell
curl "http://localhost/api/districts/5a9ec0c3ee8b0bfb4ffc18c4/facilities"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a9ec0c3ee8b0bfb4ffc18c4",
    "__v": 0,
    "updatedAt": "2018-03-06T16:28:31.000Z",
    "createdBy": "5a8b33d24456d4ad1bd97546",
    "updatedBy": "5a9ec0c3ee8b0bfb4ffc18c9",
    "createdAt": "2018-03-06T16:15:20.651Z",
    "deleted": false,
    "facilities": [
        "5a8327ffb2cc252d4bbb7d0b"
    ],
    "identifier": "5437",
    "name": "District 1"
}
```

This endpoint takes the districts's id as a query paramater, and the facility's id as a body property.

### HTTP Request

`POST http://localhost/api/districts/<id>/facilities`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
facilityId | string | true | (see <a href="#facilities">`facility`</a>)
