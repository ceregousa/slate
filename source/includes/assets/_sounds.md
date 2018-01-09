# Sounds

## Get a sound

```shell
curl https://cerego.com/api/v3/sounds/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

```json
{
  "data": {
    "id": "123456",
    "type": "sounds",
    "attributes": {
      "created-at": "2014-08-19T17:17:24.000Z",
      "url": "https://assets.cerego.com/uploads/sound/uploader/662672/h3ll0m473.mp3"
    },
    "links": {
      "self": "/v3/sounds/123456"
    }
  }
}
```

This endpoint retrieves an sound.

### HTTP Request

`GET https://cerego.com/api/v3/sounds/:id`

### Sound Object

Attribute | Type | Description
--------- | ------- | -----------
created_at | datetime | The time which the sound was created
url | string | The url for the sound

## Upload a sound

Cerego supports 3 ways of uploading an asset: via URL, File, or base64 encoded data.

### Via URL (using a miltipart form)
```shell
curl 'https://cerego.com/api/v3/sounds' 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundaryMVLbHo8cqv4TIsAb'
  -H 'accept: application/json'
  --data-binary $'------WebKitFormBoundaryMVLbHo8cqv4TIsAb\r\nContent-Disposition: form-data; name="url"\r\n\r\nhttps://www.example.com/file.mp3\r\n------WebKitFormBoundaryMVLbHo8cqv4TIsAb--\r\n'
```

### Via URL (using JSON)
```shell
curl 'https://cerego.com/api/v3/sounds' 
  -X POST 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: application/json'
  -H 'accept: application/json'
  -d '{"url":"https://www.example.com/file.mp3"}'
```

### Via File (using a miltipart form)

```shell
curl 'https://cerego.com/api/v3/sounds'
   -H 'Authorization: Bearer <BEARER_TOKEN>' 
   -H 'content-type: multipart/form-data; boundary=------WebKitFormBoundaryru7KOTWamg3KC9gw'
   -H 'accept: application/json' 
   --data-binary $'------WebKitFormBoundaryru7KOTWamg3KC9gw\r\nContent-Disposition: form-data; name="file"; filename="file.JPG"\r\nContent-Type: audio/mp3\r\n\r\n\r\n------WebKitFormBoundaryru7KOTWamg3KC9gw--\r\n'
```

### Via base64 data parameter
> Please note that for base64 uploads the `Content-Type` header must be set to the content type of the sound and not to `application/json` 

```shell
curl 'https://cerego.com/api/v3/sounds' 
  -X POST 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: audio/mp3'
  -H 'accept: application/json'
  -d '{"data":"<base64 encoded sound>"}'
```

### Sample Response
```json
{
  "data": {
    "id":"123",
    "type":"sounds",
    "attributes": {
      "created-at":"2018-01-08T23:46:55.000Z",
      "url":"https://prod.assets.cerego.com/uploads/sound/uploader/123/file.mp3",
      "alt-tag":null
    },
    "links": {
      "self":"/v3/sounds/123"
    }
  }
}
```

### List of supported Content-Types
* `audio/aiff`
* `audio/x-aiff`
* `audio/mpeg`
* `audio/x-mpeg`
* `audio/mp3`
* `audio/mpeg3`
* `audio/x-mpeg3`
* `audio/x-m4a`
* `audio/mp4`
* `audio/wav`
* `audio/x-wav`
* `audio/ogg`
* `audio/midi`
* `audio/x-mid`
* `audio/x-midi`

### List of supported extensions
* `aif`
* `aifc`
* `aiff`
* `m2a`
* `mp2`
* `mp3`
* `mp4`
* `mpa`
* `mpg`
* `mpga`
* `wav`
* `ogg`
* `mid`
* `midi`
* `kar`
* `m4a`
