# General

## Searching

```shell
curl "http://localhost/api/search?query="
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
[
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
        "createdAt": "2018-03-31T19:01:15.317Z",
        "_id": "5abfd52938cc8ca7ab6dd7bd"
    },
    {
        "name": "Simons district",
        "identifier": "54372323",
        "facilities": [],
        "createdAt": "2018-03-31T19:01:15.307Z",
        "_id": "5abfdd54803a89a862d55c4c",
        "createdBy": "5abfd52938cc8ca7ab6dd7ba",
        "updatedAt": "2018-03-31T19:11:16.973Z"
    }
]
```

This endpoint searches for a regex match of the query string `query` in

-`Users` by `firstName`,`lastName`,`email`,`nickName`  

-`Districts` by `name`,`identifier`  

-`Facilities` by `name`  


### HTTP Request

`GET http://localhost/api/search?query=simons`

### Minimum Role Required

None
