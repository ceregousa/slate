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