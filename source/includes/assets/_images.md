# Images

## Get an image

```shell
curl https://cerego.com/api/v3/images/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

```json
{
  "data": {
    "id": "123456",
    "type": "images",
    "attributes": {
      "created-at": "2014-08-19T17:17:24.000Z",
      "url": "https://assets.cerego.com/uploads/image/uploader/662672/h3ll0m473.jpg",
      "orig-url": null,
      "orig-owner": null,
      "license-id": null,
      "alt-tag": null
    },
    "links": {
      "self": "/v3/images/123456"
    }
  }
}
```

This endpoint retrieves an image.

### HTTP Request

`GET https://cerego.com/api/v3/images/:id`

### Image Object

Attribute | Type | Description
--------- | ------- | -----------
created_at | datetime | The time which the image was created
url | string | The url for the image
orig-url | string | Link to where the url was if it was downloaded by an external resource
orig-owner | string | The name of the person who originally created the image if exported externally
license-id | integer | The id for the type of license on the image
alt-tag | string | The alt message when you hover over the image

## Upload an image

Cerego supports 3 ways of uploading an asset: via URL, File, or base64 encoded data.

### Via URL (using a miltipart form)
```shell
curl 'https://cerego.com/api/v3/images' 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundaryMVLbHo8cqv4TIsAb'
  -H 'accept: application/json'
  --data-binary $'------WebKitFormBoundaryMVLbHo8cqv4TIsAb\r\nContent-Disposition: form-data; name="url"\r\n\r\nhttps://www.example.com/file.png\r\n------WebKitFormBoundaryMVLbHo8cqv4TIsAb--\r\n'
```

### Via URL (using JSON)
```shell
curl 'https://cerego.com/api/v3/images' 
  -X POST 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: application/json'
  -H 'accept: application/json'
  -d '{"url":"https://www.example.com/file.png"}'
```

### Via File (using a miltipart form)

```shell
curl 'https://cerego.com/api/v3/images'
   -H 'Authorization: Bearer <BEARER_TOKEN>' 
   -H 'content-type: multipart/form-data; boundary=------WebKitFormBoundaryru7KOTWamg3KC9gw'
   -H 'accept: application/json' 
   --data-binary $'------WebKitFormBoundaryru7KOTWamg3KC9gw\r\nContent-Disposition: form-data; name="file"; filename="file.JPG"\r\nContent-Type: image/jpeg\r\n\r\n\r\n------WebKitFormBoundaryru7KOTWamg3KC9gw--\r\n'
```

### Via base64 data parameter
> Please note that for base64 uploads the `Content-Type` header must be set to the content type of the image and not to `application/json` 

```shell
curl 'https://cerego.com/api/v3/images' 
  -X POST 
  -H 'authorization: Bearer <BEARER_TOKEN>' 
  -H 'content-type: image/jpeg'
  -H 'accept: application/json'
  -d '{"data":"<base64 encoded image>"}'
```

### Sample Response
```json
{
  "data": {
    "id":"123",
    "type":"images",
    "attributes": {
      "created-at":"2018-01-08T23:46:55.000Z",
      "url":"https://prod.assets.cerego.com/uploads/image/uploader/123/file.JPG",
      "orig-url":null,
      "orig-owner":null,
      "license-id":null,
      "alt-tag":null
    },
    "links": {
      "self":"/v3/images/123"
    }
  }
}
```

### List of supported Content-Types
* `image/gif`
* `image/jpg`
* `image/jpeg`
* `image/pjpeg`
* `image/png`
* `image/svg+xml`
* `image/tiff`
* `image/x-icon`
* `image/bmp`
* `image/x-bmp`
* `image/x-ms-bmp`
* `image/x-windows-bmp`
* `image/webp`

### List of supported extensions
* `gif`
* `jpg`
* `jpeg`
* `jpe`
* `png`
* `svg`
* `svgz`
* `tif`
* `tiff`
* `ico`
* `bm`
* `bmp`
* `webp`
