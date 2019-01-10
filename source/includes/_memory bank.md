# Memory Bank

<aside class="warning">V2 Memory Bank endpoints will be deprecated in late 2019</aside>

## Show Items

```shell
curl https://cerego.com/api/v2/users/:user_id/sets/:set_id/items_memory_bank
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

```shell
curl https://cerego.com/api/v2/users/:user_id/series/:series_id/items_memory_bank
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> The above commands return JSON structured like this:

```json
{
  "meta" : {
    "message" : "OK",
    "status" : 200
  },
  "response" : [
    {
      "learning_engine_guid" : "eca5919b-084e-46b8-914e-f0afbc194485",
      "difficulty_bucket" : 1,
      "level" : 0.7446,
      "accuracy" : 1,
      "presentations_count" : 1,
      "total_study_time_millis" : 6697,
      "last_study_time" : "2018-08-09T17:21:56.000Z",
      "see_next_at" : "2018-08-10T09:26:21.000Z",
      "review_interval" : 57865309,
      "current_retention" : 0,
      "easiness_modifier" : 0.8947
    },
    {
      "learning_engine_guid" : "ce89723f-8f43-44a6-bc99-6fea96f775eb",
      "difficulty_bucket" : 1,
      "level" : 0.854,
      "accuracy" : 1,
      "presentations_count" : 1,
      "total_study_time_millis" : 6100,
      "last_study_time" : "2018-08-09T17:22:02.000Z",
      "see_next_at" : "2018-08-10T12:27:07.000Z",
      "review_interval" : 68704872,
      "current_retention" : 0,
      "easiness_modifier" : 0.8954
    },
    ...
  ]
}
```

These endpoints retrieve the items in the memory bank for a given set/series.

### HTTP Request

`GET https://cerego.com/api/v2/users/:user_id/sets/:set_id/items_memory_bank`

`GET https://cerego.com/api/v2/users/:user_id/series/:series_id/items_memory_bank`

### Memory Object

Attribute | type | Description
--------- | --------- | -----------
learning_engine_guid | string | a guid of the item
difficulty_bucket | integer | average difficulty of the item (between 0 and 3)
level | float | a value that maps to how long the user will remember the item
accuracy | integer | ratio of how often the item is answered correctly (between 0 and 1)
presentations_count | integer | number of times the item has been displayed to user
total_study_time_millis | integer | total time the item has been studied (in millis)
last_study_time | datetime | the last time the item was studied
see_next_at | datetime | the optimum time for the user to review the item
review_interval | integer | the interval in milliseconds required for the items to reach target retention
current_retention | integer | the probability that the item will be recalled
easiness_modifier | float | difficulty factor of this item for the user

### Meta

Attribute | type | Description
--------- | --------- | -----------
message | string | http response message
status | integer | http response status code

## Show Goals

```shell
curl https://cerego.com/api/v2/users/:user_id/goals_memory_bank
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

```shell
curl https://cerego.com/api/v2/users/:user_id/series/:series_id/goals_memory_bank
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> The above commands return JSON structured like this:

```json
{
  "meta": {
    "status": 200,
    "message": "OK"
  },
  "response": [
    {
      "id" : 887552,
      "name" : "Read Thai",
      "module_type" : "set",
      "image" : "https://assets-cerego-com.s3-us-west-2.amazonaws.com/uploads/image/uploader/710474/c15v8h221n9cas.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIP7EH7E47533LFOA%2F20190104%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20190104T192419Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=aaa4f716f0b740b3bc87e31abe78cf4a3273ab3b5573a2c54d2127b7d71a697c",
      "remixed" : false,
      "items_count" : 100,
      "studied_items_count" : 18,
      "eligible_items_count" : 18,
      "total_ic_count" : 0,
      "seen_ic_count" : 0,
      "presentations_count" : 144,
      "difficulty_bucket" : 0,
      "scoring_goal" : 1,
      "level" : 0.7883,
      "score" : 0.1419,
      "progress" : 0.1419,
      "accuracy" : 0.5176,
      "total_study_time_millis" : 1900256,
      "last_study_time" : "2018-11-27T06:13:50.000Z",
      "see_next_at" : "2018-11-26T23:00:11.000Z",
      "due_ats" : [
         "2018-12-01T07:59:59.000Z"
      ],
      "average_current_retention" : 0.0211,
      "average_review_interval" : 60657181,
      "average_easiness_modifier" : 0.9019,
      "items_in_level" : {
         "0" : 0,
         "5" : 0,
         "3" : 0,
         "new" : 8,
         "4" : 0,
         "1" : 10,
         "2" : 0
      }
    },
    {
      "id": 841345,
      "name": "Ireland's Counties",
      "module_type": "set",
      "image": "https://assets-cerego-com.s3-us-west-2.amazonaws.com/uploads/image/uploader/1285965/harp.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIP7EH7E47533LFOA%2F20190104%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20190104T014506Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=d651b35ffb2773b02301cbea9cb1c10af3b5c33f27821bf7c099b66a80f9edaf",
      "remixed": false,
      "items_in_level": {
        "0": 1,
        "1": 20,
        "2": 2,
        "3": 0,
        "4": 0,
        "5": 0,
        "new": 18
      },
      "items_count": 41,
      "studied_items_count": 41,
      "eligible_items_count": 23,
      "total_ic_count": 0,
      "seen_ic_count": 0,
      "level": 0.8923,
      "score": 0.8923,
      "progress": 0.2974,
      "scoring_goal": 3,
      "due_ats": [],
      "difficulty_bucket": 1,
      "last_study_time": "2019-01-04T01:45:00.000Z",
      "see_next_at": "2018-05-17T15:34:26.000Z",
      "total_study_time_millis": 2676337,
      "accuracy": 0.3738,
      "presentations_count": 180,
      "average_review_interval": 72220893,
      "average_current_retention": 0.439,
      "average_easiness_modifier": 0.8802
    },
    ...
  ]
}
```

These endpoints retrieve the goals in the memory bank for a specified user. (Can be constrained by sets within a given series)

### HTTP Request

`GET https://cerego.com/api/v2/users/:user_id/goals_memory_bank`

`GET https://cerego.com/api/v2/users/:user_id/series/:series_id/goals_memory_bank`

### Memory Object

Attribute | type | Description
--------- | ---- | -----------
id | integer | the id of the set
name | string | the name of the set
module_type | string | the module type, always a "set" here
image | string | url to the set's icon image
remixed | boolean | whether the set is remixed or not
items_count | integer | total number of items in the set
studied_items_count | integer | number of items that have been studied at least once by the user
eligible_items_count | integer | number of items that have faded and are ready to review
total_ic_count | integer | total number of instructional items in the set
seen_ic_count | integer | number of instructional items seen by the user
presentations_count | integer | number of times the set has been displayed to user
difficulty_bucket | integer | average difficulty of items for the set (between 0 and 3)
level | float | a value that maps to how long the user will remember all items in the set
score | float | the level adjusted for unstarted items
scoring_goal | integer | the level as a goal determined by the set creator
progress | float | progress towards the scoring_goal
accuracy | float | ratio of how often items are answered correctly (between 0 and 1)
total_study_time_millis | integer | total amount of time spent studying the set
last_study_time | datetime | time the item was last studied
see_next_at | datetime | the optimum time for the user to review the set
due_ats | datetime[] | an array of dates for sets with a due date
average_review_interval | integer | the interval in milliseconds required for the items to reach target retention
average_current_retention | integer | the probability that the set's items will be recalled
average_easiness_modifier | integer | difficulty factor of this set for this user

### Items in level Object

Attribute | type | Description
--------- | ---- | -----------
0 | integer | number of items with a level < 1
1 | integer | number of items with a level >= 1 and < 2
2 | integer | number of items with a level >= 2 and < 3
3 | integer | number of items with a level >= 3 and < 4
4 | integer | number of items with a level >= 4 and < 5
5 | integer | number of items with a level >= 5
new | integer | number of items not yet studied


### Meta

Attribute | type | Description
--------- | --------- | -----------
message | string | http response message
status | integer | http response status code
