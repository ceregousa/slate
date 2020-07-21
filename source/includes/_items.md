# Items

## List all items in a set

```shell
curl https://cerego.com/api/v3/sets/:id/items
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1166905",
      "type": "items",
      "attributes": {
        "created-at": "2016-04-19T01:56:06.000Z",
        "study-type": "study",
        "note-type": "item",
        "note-tab-text": null,
        "explanation-type": null,
        "is-studiable": true,
        "template-type": "vocabulary",
        "title": null
      },
      "relationships": {
        "facets": {
          "data": [
            {
              "id": "1453103",
              "type": "facets"
            }
          ]
        },
        "annotations": {
          "data": []
        },
        "sentences": {
          "data": []
        }
      },
      "links": {
        "self": "/v3/items/1166905"
      }
    },
    ...
  ],
  "links": {
    "self": "https://cerego.com/api/v3/sets/123456/items?page%5Bnumber%5D=1&page%5Bsize%5D=15",
    "next": "https://cerego.com/api/v3/sets/123456/items?page%5Bnumber%5D=2&page%5Bsize%5D=15",
    "last": "https://cerego.com/api/v3/sets/123456/items?page%5Bnumber%5D=4&page%5Bsize%5D=15"
  },
  "meta": {
    "total-pages": 4,
    "total-count": 53
  }
}
```

This endpoint retrieves all items within a specific set.

### HTTP Request

`GET https://cerego.com/api/v3/sets/:id/items`

### Item Object

Attribute | type | Templates | Description
--------- | ---- | --------- | -----------
created_at | datetime | All | When the item was created
template_type | enum | All | `associations` (flashcards), `vocabulary`, `passages`, `regions`, `sequences`, `patterns`, `application_questions`,  `question_and_answers`, or `instructional_contents`
is_studiable | bool | All | Whether or not the item will be made available for study
text | string | passages | The full text of the passage
title | string | regions, patterns, sequences, instrustructional_contents | The title of the item 
answer_type | enum | application_questions, question_and_answers | `single_correct` (default) or `multi_correct`
explanation_type | enum | application_questions, question_and_answers | `explain_item` (default)  or `explain_facet`
ic_subtype | enum | instructional_contents | `instructional_embed`, `instructional_document`, or `instructional_page`
note_type | enum | All except instructional_contents | `item` (default) or `facet`
note_tab_text | string | All except instructional_contents | If set will override the default of "Notes"
study_type | enum | All except instructional_contents | `study` (default), `notes` or `none` 

<aside class="notice">Not all attributes are valid for all templates.  Please check the template_type first to see which attributes can be expected.</aside>

<aside class="notice">Instructional Contents have three subtypes, but all three are identical as far as the API response is concerned.  Each subtype however will return a different type of Annotation object in the relationships.</aside>

<aside class="notice">Templates are not required for an item to exist, you can create "placeholder" items before you know which template you will require, and then later update them.</aside>

Relationship | type | Templates | Description
------------ | ---- | --------- | -----------
image | images | regions, passages | Attached image 
facets | facets | All except instructional_contents | Array of facets (links between a `front` and `back`) for the item
annotations | annotations | All except instructional_contents | Array of notes attached to the item
sentences | sentences | vocabulary | Array of sentences attached to the vocabulary item
attached_items | items | application_questions, question_and_answers | Array of instructional_contents attached to the item

<aside class="notice">Not all relationships are valid for all templates.  Please check the template_type first to see which relationships can be expected.</aside>

## Get an item

```shell
curl https://cerego.com/api/v3/items/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3205069",
    "type": "items",
    "attributes": {
      "created-at": "2018-08-21T21:54:20.000Z",
      "study-type": "study",
      "note-type": "item",
      "note-tab-text": null,
      "explanation-type": null,
      "is-studiable": false,
      "template-type": "associations",
      "title": null
    },
    "relationships": {
      "facets": {
        "data": []
      },
      "annotations": {
        "data": []
      },
      "sentences": {
        "data": []
      }
    },
    "links": {
      "self": "/v3/items/3205069"
    }
  }
}
```

This endpoint retrieves one item.

### HTTP Request

`GET https://cerego.com/api/v3/items/:id`

## Create an item

```shell
curl https://cerego.com/api/v3/sets/:id/items
    -d '{"data":{"attributes":{"position":1}}}'
    -X POST
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3205068",
    "type": "items",
    "attributes": {
      "created-at": "2018-08-21T21:54:18.000Z",
      "study-type": "study",
      "note-type": "item",
      "note-tab-text": null,
      "explanation-type": null,
      "is-studiable": false
    },
    "relationships": {
      "facets": {
        "data": []
      },
      "annotations": {
        "data": []
      },
      "sentences": {
        "data": []
      }
    },
    "links": {
      "self": "/v3/items/3205068"
    }
  }
}
```

This endpoint create one item within a specific set.

### HTTP Request

`POST https://cerego.com/api/v3/sets/:id/items`

## Update an item

```shell
curl https://cerego.com/api/v3/items/:id
    -d '{ "id":3205069, "type":"items","attributes":{ "created-at":"2018-08-21T21:54:20.000Z","study-type":"study","note-type":"item","note-tab-text":null,"explanation-type":null,"is-studiable":false},"relationships":{"facets":{"data":[]},"annotations":{"data":[]},"sentences":{"data":[]}},"links":{"self":"/v3/items/3205069"},"selected":true,"expanded":true,"errors":["missing_template"],"cardState":"no_template","card":{},"data":{"attributes":{"template-type":"associations"}}}'
    -X PUT
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

```json
{
  "data": {
    "id": "3205069",
    "type": "items",
    "attributes": {
      "created-at": "2018-08-21T21:54:20.000Z",
      "study-type": "study",
      "note-type": "item",
      "note-tab-text": null,
      "explanation-type": null,
      "is-studiable": false,
      "template-type": "associations",
      "title": null
    },
    "relationships": {
      "facets": {
        "data": []
      },
      "annotations": {
        "data": []
      },
      "sentences": {
        "data": []
      }
    },
    "links": {
      "self": "/v3/items/3205069"
    }
  }
}
```

This endpoint updates one item.

### HTTP Request

`PUT https://cerego.com/api/v3/items/:id`

## Delete an item

```shell
curl https://cerego.com/api/v3/items/:id
    -X DELETE
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your DELETE request you should receive a 204 No Content

This endpoint removes one item.

### HTTP Request

`DELETE https://cerego.com/api/v3/items/:id`

## Clone an item

```shell
curl https://cerego.com/api/v3/items/:id/clone
    -d '{"data":{"attributes":{"target-set-id":123456,"position":2}}}'
    -X POST
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "3205068",
    "type": "items",
    "attributes": {
      "created-at": "2018-08-21T21:54:18.000Z",
      "study-type": "study",
      "note-type": "item",
      "note-tab-text": null,
      "explanation-type": null,
      "is-studiable": false
    },
    "relationships": {
      "facets": {
        "data": []
      },
      "annotations": {
        "data": []
      },
      "sentences": {
        "data": []
      }
    },
    "links": {
      "self": "/v3/items/3205068"
    }
  }
}
```


This endpoint clones one item into a specific set.

<aside class="notice">The `target-set-id` parameter is optional, if ommitted the item will be closed into the same set within which it already exists.</aside>

### HTTP Request

`POST https://cerego.com/api/v3/items/:id/clone`
