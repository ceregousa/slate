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