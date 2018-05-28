# Shared Sensor Sets

## Create a new set

```shell
curl "http://localhost/api/facilities/5ad14af26ee7f3506ffe38b4/sensorsets"
  -H "Authorization: Bearer {token}"
```

> Payload sample

```json
{
	"name":"SetA",
	"sensors": [
		{
			"type": 0,
    		"unitNumber": 1,
    		"unitID": 67434
    	},
    	{
			"type": 1,
    		"unitNumber": 5,
    		"unitID": 2345
    	},
    	{
			"type": 0,
    		"unitNumber": 2,
    		"unitID": 4634
    	},
    	{
			"type": 2,
    		"unitNumber": 3,
    		"unitID": 532
    	}
	]
}
```

> Example Response

```json
{
    "createdAt": "2018-05-28T18:22:06.395Z",
    "_id": "5b0c493686cd5d8a116a7760",
    "name": "SetA",
    "sensors": [
        {
            "_id": "5b0c493686cd5d8a116a7764",
            "type": 0,
            "unitNumber": 1,
            "unitID": 67434
        },
        {
            "_id": "5b0c493686cd5d8a116a7763",
            "type": 1,
            "unitNumber": 5,
            "unitID": 2345
        },
        {
            "_id": "5b0c493686cd5d8a116a7762",
            "type": 0,
            "unitNumber": 2,
            "unitID": 4634
        },
        {
            "_id": "5b0c493686cd5d8a116a7761",
            "type": 2,
            "unitNumber": 3,
            "unitID": 532
        }
    ],
    "createdBy": "5ace8cad554ec367308ffcae",
    "updatedAt": "2018-05-28T18:23:50.856Z"
}
```

### HTTP Request

`POST http://localhost/api/facilities/<id>/sensorsets`






## Update a set

```shell
curl "http://localhost/api/facilities/5ad14af26ee7f3506ffe38b4/sensorsets/5b0c493686cd5d8a116a7760"
  -H "Authorization: Bearer {token}"
```

> Payload sample

```json
{
	"name": "New set name",
	"sensors": [
    	{
			"type": 0,
    		"unitNumber": 2,
    		"unitID": 2342
    	},
    	{
			"type": 1,
    		"unitNumber": 9,
    		"unitID": 976
    	}
	]
}
```

> Example Response

```json
{
    "createdAt": "2018-05-28T18:22:06.395Z",
    "sensors": [
        {
            "_id": "5b0c4d16efe9088a9946de76",
            "type": 0,
            "unitNumber": 2,
            "unitID": 2342
        },
        {
            "_id": "5b0c4d16efe9088a9946de75",
            "type": 1,
            "unitNumber": 9,
            "unitID": 976
        }
    ],
    "_id": "5b0c493686cd5d8a116a7760",
    "name": "New set name",
    "createdBy": "5ace8cad554ec367308ffcae",
    "updatedAt": "2018-05-28T18:40:22.000Z"
}
```

You should perform a `GET` request and make changes to the returned `sensor` array before doing this `PUT` request. The new sensor array within this body will replace the existing one.

### HTTP Request

`PUT http://localhost/api/facilities/<id>/sensorsets/<sensor_set_id>`







## Get a set

```shell
curl "http://localhost/api/facilities/5ad14af26ee7f3506ffe38b4/sensorsets/5b0c493686cd5d8a116a7760"
  -H "Authorization: Bearer {token}"
```

> Example Response

```json
{
    "createdAt": "2018-05-28T18:22:06.395Z",
    "sensors": [
        {
            "_id": "5b0c493686cd5d8a116a7764",
            "type": 0,
            "unitNumber": 1,
            "unitID": 67434
        },
        {
            "_id": "5b0c493686cd5d8a116a7763",
            "type": 1,
            "unitNumber": 5,
            "unitID": 2345
        },
        {
            "_id": "5b0c493686cd5d8a116a7762",
            "type": 0,
            "unitNumber": 2,
            "unitID": 4634
        },
        {
            "_id": "5b0c493686cd5d8a116a7761",
            "type": 2,
            "unitNumber": 3,
            "unitID": 532
        }
    ],
    "_id": "5b0c493686cd5d8a116a7760",
    "name": "SetA",
    "createdBy": "5ace8cad554ec367308ffcae",
    "updatedAt": "2018-05-28T18:23:50.856Z"
}
```

### HTTP Request

`GET http://localhost/api/facilities/<id>/sensorsets/<sensor_set_id>`



## Get all sensor sets for a facility

```shell
curl "http://localhost/api/facilities/5ad14af26ee7f3506ffe38b4/sensorsets"
  -H "Authorization: Bearer {token}"
```

> Example Response

```json
[
    {
        "createdAt": "2018-05-28T18:54:22.255Z",
        "sensors": [
            {
                "_id": "5b0c5062b7d9d18bf3916131",
                "type": 0,
                "unitNumber": 1,
                "unitID": 67434
            },
            {
                "_id": "5b0c5062b7d9d18bf3916130",
                "type": 1,
                "unitNumber": 5,
                "unitID": 2345
            },
            {
                "_id": "5b0c5062b7d9d18bf391612f",
                "type": 0,
                "unitNumber": 2,
                "unitID": 4634
            },
            {
                "_id": "5b0c5062b7d9d18bf391612e",
                "type": 2,
                "unitNumber": 3,
                "unitID": 532
            }
        ],
        "_id": "5b0c5062b7d9d18bf391612d",
        "name": "SetA",
        "createdBy": "5ace8cad554ec367308ffcae",
        "updatedAt": "2018-05-28T18:54:26.197Z"
    },
    {
        "createdAt": "2018-05-28T18:54:22.255Z",
        "sensors": [
            {
                "_id": "5b0c5088b7d9d18bf3916141",
                "type": 0,
                "unitNumber": 1,
                "unitID": 423
            },
            {
                "_id": "5b0c5088b7d9d18bf3916140",
                "type": 1,
                "unitNumber": 5,
                "unitID": 754
            },
            {
                "_id": "5b0c5088b7d9d18bf391613f",
                "type": 0,
                "unitNumber": 2,
                "unitID": 123
            },
            {
                "_id": "5b0c5088b7d9d18bf391613e",
                "type": 2,
                "unitNumber": 3,
                "unitID": 87
            }
        ],
        "_id": "5b0c5088b7d9d18bf391613d",
        "name": "SetB",
        "createdBy": "5ace8cad554ec367308ffcae",
        "updatedAt": "2018-05-28T18:55:04.109Z"
    }
]
```

### HTTP Request

`GET http://localhost/api/facilities/<id>/sensorsets`






## Delete a sensor set

```shell
curl "http://localhost/api/facilities/5ad14af26ee7f3506ffe38b4/sensorsets/5b0c5062b7d9d18bf391612d"
  -H "Authorization: Bearer {token}"
```

> Example Response

```json
{
    "message": "Sensor set deleted."
}
```

### HTTP Request

`DELETE http://localhost/api/facilities/<id>/sensorsets/<sensor_set_id>`
