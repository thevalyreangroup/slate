# Mobile

## Upload/Sync Participant Metric Data

```shell
curl "http://localhost/api/sync"
  -H "Authorization: Bearer {token}"
```

> The above command returns 200 whether any failures or errors were found or not.

> Payload sample

```json
[
  {
    "class":{
      "id":"5acd6d73a58fd80fcb493dc0",
      "sampleInterval": 1,
      "duration": 19,
      "updateZones": true,
      "participants":[
        {
          "id": "5acd6d73a58fd80fcb493dc0",
          "fieldIdentifiers": ["HR", "PWR", "RPM"],
          "devices": [
            {
              "HRM": {
                "deviceId": 1234
              }
            },
            {  
              "BPWR":{
                "deviceId": 3425
              }
            },
            {
              "BSC":{
                "deviceId": 44673
              }
            }
          ],
          "HR": {
            "title": "Heart Rate",
            "units": "bpm",
            "source": "HRM",
            "zone": "threshold",
            "shr": 40,
            "t1": 200,
            "t2": 540,
            "peak": 920
          },
          "PWR": {
            "title": "Power",
            "units": "watts",
            "source": "BPWR"
          },
          "RPM": {
            "title": "Rotations Per Minute",
            "units": "rpm",
            "source": "BSC"
          },
          "fieldOrder": ["HR", "PWR", "RPM"],
          "records":[
            {"record": [123, 79, 98]},
            {"record": [124, 79, 98]},
            {"record": [123, 79, 97]},
            {"record": [126, 80, 97]}
          ]
        },
        {
          "id": "5acd6d73a58fd80fcb493dc1",
          "fieldIdentifiers": ["HR", "PWR", "RPM"],
          "devices": [
            {
              "HRM": {
                "deviceId": 4532
              }
            },
            {  
              "BPWR":{
                "deviceId": 34634
              }
            },
            {
              "BSC":{
                "deviceId": 2525
              }
            }
          ],
          "HR": {
            "title": "Heart Rate",
            "units": "bpm",
            "source": "HRM",
            "zone": "threshold",
            "shr": 80,
            "t1": 135,
            "t2": 184,
            "peak": 198
          },
          "PWR": {
            "title": "Power",
            "units": "watts",
            "source": "BPWR"
          },
          "RPM": {
            "title": "Rotations Per Minute",
            "units": "rpm",
            "source": "BSC"
          },
          "fieldOrder": ["HR", "PWR", "RPM"],
          "records":[
            {"record": [123, 79, 98]},
            {"record": [124, 79, 98]},
            {"record": [123, 79, 97]},
            {"record": [126, 80, 97]}
          ]
        }
      ]
    }
  }
]
```

> Example Total Failure

```json
{
    "errors": [
        {
            "message": "Participant failed to save.",
            "id": "5acd6d73a58fd80fcb493dc0",
            "reason": "Participant not found, check the ID.",
            "result": "Participant Skipped"
        },
        {
            "message": "Participant failed to prepare for saving.",
            "id": "5acd6d73a58fd80fcb493dc1",
            "reason": "Malformed metrics data.",
            "result": "Participant Skipped"
        }
    ],
    "saved": 0,
    "failed": 2
}
```

> Example success

```json
{
    "errors": [],
    "saved": 2,
    "failed": 0
}
```

When multiple participants or classes are passed in, the API will parse all of them synchronously and skip any failures. Some may fail, while some may succeed. You should monitor the response for the necessary error messages and results.

### HTTP Request

`POST http://localhost/api/sync`
