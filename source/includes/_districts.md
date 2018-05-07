# Districts

## Create a District

```shell
curl "http://localhost/api/districts"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "name": "District 9",
    "identifier": "54372323",
    "facilities": [],
    "createdAt": "2018-03-31T19:53:34.876Z",
    "_id": "5abfe75d9ca354a9e7faa2fc",
    "createdBy": "5abfdeac21aa27a8d32edb94",
    "updatedAt": "2018-03-31T19:54:05.688Z"
}
```

This endpoint creates a new district.

### HTTP Request

`POST http://localhost/api/districts`

### Minimum Role Required

`SALES_SUPPORT`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | true |
identifier | string | true |
address | Address | false | (see <a href="#address">`ADDRESS`</a>)

## Get all Districts

```shell
curl "http://localhost/api/districts"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "name": "District 1",
        "identifier": "5437",
        "facilities": [
            {
                "name": "test facility 1",
                "type": 0,
                "createdAt": "2018-02-13T17:50:03.778Z",
                "_id": "5abfe7efdcb36ea9f1fa7c02",
                "__v": 0,
                "updatedAt": "2018-02-13T18:01:35.815Z",
                "createdBy": "5a75ee8b4b8d5fd5797d0863"
            }
        ],
        "createdAt": "2018-03-06T16:15:20.651Z",
        "_id": "5abfe7efdcb36ea9f1fa7c0c",
        "updatedAt": "2018-03-31T20:00:31.000Z",
        "createdBy": "5a8b33d24456d4ad1bd97546",
        "updatedBy": "5abfe7efdcb36ea9f1fa7c11"
    },
    {
        "name": "District 2",
        "identifier": "344347",
        "facilities": [],
        "createdAt": "2018-03-06T16:15:20.651Z",
        "_id": "5abfe7efdcb36ea9f1fa7c0d",
        "updatedAt": "2018-03-06T16:15:22.756Z",
        "createdBy": "5a8b33d24456d4ad1bd97546"
    }
]
```

This endpoint returns all districts registered.

### HTTP Request

`GET http://localhost/api/districts`

### Minimum Role Required

`SALES_SUPPORT`

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

### Minimum Role Required

`SALES_SUPPORT`

## Update a District

```shell
curl "http://localhost/api/districts/5a9ec0c3ee8b0bfb4ffc18c5"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "_id": "5a9ec0c3ee8b0bfb4ffc18c4",
    "updatedAt": "2018-03-06T16:28:31.000Z",
    "createdBy": "5a8b33d24456d4ad1bd97546",
    "updatedBy": "5a9ec0c3ee8b0bfb4ffc18c9",
    "createdAt": "2018-03-06T16:15:20.651Z",
    "facilities": [],
    "identifier": "5437",
    "name": "District 1"
}
```

This endpoint takes the districts's id as a query paramater and returns the new participant object after saving.

### HTTP Request

`PUT http://localhost/api/facilities/<id>`

### Minimum Role Required

`DISTRICT_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
name | string | false |
identifier | integer | false |
address | Address | false | (see <a href="#address">`ADDRESS`</a>)

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

This endpoint takes the districts's id as a query parameter, and the facility's id as a body property.

### HTTP Request

`POST http://localhost/api/districts/<id>/facilities`

### Minimum Role Required

`DISTRICT_ADMIN`

### Payload parameters

Parameter | Type | Required | Description
--------- | ---- | -------- | -----------
facilityId | string | true | (see <a href="#facilities">`facility`</a>)
