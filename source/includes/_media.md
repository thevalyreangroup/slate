# Media

## Save file

```shell
curl "http://localhost/api/media/testFileName.csv"
  -H "Authorization: Bearer {token}"
```

> The above command returns an empty response if succesful:

```json

```

This endpoint uploads (or updates) a file on an AWS S3 Bucket.

### HTTP Request

`POST http://localhost/api/media/<file_name>`

### Payload parameters

Parameter | Type
--------- | ----
file | form_data

<aside class="success">
If you are updating a file, the API uses a combination of the filename and user ID to decide if it exists. A user may not have two of the same file names.
</aside>

## Get metadata for a file

```shell
curl "http://localhost/api/media/info/testfilename12.csv"
  -H "Authorization: Bearer {token}"
```

> The above command returns JSON structured like this:

```json
{
    "LastModified": "2018-02-13T00:29:44.000Z",
    "ContentLength": 90,
    "ContentType": "application/octet-stream",
    "awsURL": "https://s3.amazonaws.com/heartzones_app_uploads/testfilename.jpg",
    "fileName": "testfilename12.csv",
    "createdBy": "tony simons",
    "createdAt": "2018-02-13T00:29:32.463Z",
    "updatedBy": "tony simons",
    "updatedAt": "2018-02-13T00:29:32.463Z",
}
```

This endpoint takes the file's name as a URL parameter and returns the necessary metadata for the file. The `awsURL` can be used to physically download the file.

### HTTP Request

`GET http://localhost/api/media/info/<file_name>`
