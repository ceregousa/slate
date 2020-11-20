# User Tags

## Add a tag to a user

```shell
curl https://partners.cerego.com/v3/partner_user_tag_types/:tag_type_id/partner_user_tags \
    -d '{"user_id": "1185304", "value": "The value of the tag"}' \
    -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "84918",
    "type": "partner-user-tags",
    "attributes": {
      "value": "The value of the tag",
      "created-at": "2020-11-19T00:14:19.000Z",
      "updated-at": "2020-11-19T00:14:19.000Z"
    },
    "relationships": {
      "user": {
        "data": {
          "id": "1185304",
          "type": "users"
        }
      },
      "partner-user-tag-type": {
        "data": {
          "id": "3",
          "type": "partner-user-tag-types"
        }
      }
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

This endpoint adds a tag to a user. When using this, you specify the tag_type_id and the value to set. Tag types must be set up for your account ahead of time. Contact your customer support representative to know the ids for your account's tag types.   

### HTTP Request

`POST https://partners.cerego.com/v3/partner_user_tag_types/:tag_type_id/partner_user_tags`

### Request Parameters

Parameter | Type | Required? | Description
--------- | --------- | --------- | -----------
user_id | string | yes | The ID of the user
value | string | yes | The value of the tag

<aside class="warning">This endpoint will create a tag for a user for a tag type only if the user doesn't have a tag for that tag type yet. This endpoint can't be used to update tag values.</aside>

## Update a user's tag

```shell
curl https://partners.cerego.com/v3/partner_user_tags/:id \
    -d '{"value": "The value of the tag"}' \
    -X PUT \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your PUT request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "84918",
    "type": "partner-user-tags",
    "attributes": {
      "value": "The value of the tag",
      "created-at": "2020-11-19T00:14:19.000Z",
      "updated-at": "2020-11-19T00:14:19.000Z"
    },
    "relationships": {
      "user": {
        "data": {
          "id": "1185304",
          "type": "users"
        }
      },
      "partner-user-tag-type": {
        "data": {
          "id": "3",
          "type": "partner-user-tag-types"
        }
      }
    }
  },
  "meta": {
    "total-pages": null,
    "total-count": null
  }
}
```

This endpoint updates a user's tag

### HTTP Request

`PUT https://partners.cerego.com/v3/partner_user_tags/:id`


### Request Parameters

Parameter | Type | Required? | Description
--------- | --------- | --------- | -----------
value | string | yes | The value of the tag

