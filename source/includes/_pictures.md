# Pictures

## Upload

```shell
curl "http://localhost/api/users/image/5a72027f4bf51fa978b29033"
  -H "Authorization: Bearer {token}"
```

> The above command returns the following response if succesful:

```json
{
    "message": "Image saved successfully."
}
```

This endpoint uploads (or updates) the picture stored for the entity. Image content types should be JPEG or PNG.

### HTTP Request

`POST http://localhost/api/users/image/<id>`
`POST http://localhost/api/facilities/image/<id>`

### Payload parameters

Parameter | Type
--------- | ----
file | form_data


## Get PNG representation

```shell
curl "http://localhost/api/facilities/image/5a72027f4bf51fa978b29033?token=23113cd0-1015-11e8-8571-b59c57efe38a"
```

> The above command returns a PNG representation of the stored image data.

```

```

This endpoint takes the entity's ID as a URL parameter and returns the necessary a PNG file. The bearer token must be provided in the `token` query string.

### HTTP Request

`GET http://localhost/api/users/image/<id>?token={bearer token}`
`GET http://localhost/api/facilities/image/<id>?token={bearer token}`
