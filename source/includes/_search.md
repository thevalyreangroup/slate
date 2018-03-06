# Search

## Search

```shell
curl "http://localhost/api/districts?query=5437"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18c7",
        "__v": 0,
        "updatedAt": "2018-03-06T16:15:22.756Z",
        "createdBy": "5a8b33d24456d4ad1bd97546",
        "createdAt": "2018-03-06T16:15:20.651Z",
        "deleted": false,
        "facilities": [],
        "identifier": "5412385437",
        "name": "District 4"
    },
    {
        "_id": "5a9ec0c3ee8b0bfb4ffc18c4",
        "__v": 0,
        "updatedAt": "2018-03-06T16:28:31.000Z",
        "createdBy": "5a8b33d24456d4ad1bd97546",
        "updatedBy": "5a9ec0c3ee8b0bfb4ffc18c9",
        "createdAt": "2018-03-06T16:15:20.651Z",
        "deleted": false,
        "facilities": [
            "5a8b281ee3c022a8d0cf74a7"
        ],
        "identifier": "5437",
        "name": "District 1"
    }
]
```

This endpoint searches the database models of `Users`,`Facilities`,`Districts`, and `Participants` and returns all possible matches of the query string.

### HTTP Request

`GET http://localhost/api/search?query=`
