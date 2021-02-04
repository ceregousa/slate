# Assignments

## Get the assignments in a course

```shell
curl https://partners.cerego.com/v3/courses/:id/assignments
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1002204",
      "type": "sets",
      "attributes": {
        "created-at": "2021-02-02T19:48:36.000Z",
        "slug": "introduction-e199d4e9-fa2a-42c2-9e01-b03992cb99ff",
        "name": "Introduction",
        "description": null,
        "description-html": null,
        "is-featured": false,
        "items-count": 4,
        "memories-count": 4,
        "studiable-items-count": 4,
        "studiable-memories-count": 4,
        "content-updated-at": "2021-02-02T19:48:42.000Z",
        "remixable-type": null,
        "remixed-only": null,
        "ic-items-count": 1,
        "study-time-in-sec": 80,
        "scorm-package-id": null,
        "course-information": null,
        "learn-version": 4,
        "goal-type": "set",
        "is-shared": false
      },
      "relationships": {
        "privacy-type": {
          "data": {
            "id": 1,
            "name": "Private"
          }
        },
        "image": {
          "data": null
        },
        "language": {
          "data": {
            "id": "1819",
            "type": "languages"
          }
        },
        "response-language": {
          "data": {
            "id": "1819",
            "type": "languages"
          }
        },
        "creator": {
          "data": {
            "id": "21",
            "type": "partners"
          }
        },
        "characteristics": {
          "data": []
        },
        "parent-set": {
          "data": null
        }
      },
      "links": {
        "self": "/v3/courses/okdxe9m7/sets/1002204"
      },
      "meta": {
        "can-edit": true,
        "due-at": null,
        "course-set-created-at": "2021-02-02T19:48:37.000Z",
        "level-goal": 1.0,
        "position": 1,
        "published": false,
        "publish-at": null,
        "prereq-assignment-id": null,
        "prereq-type": null,
        "prereq-value": null,
        "assignment-id": 2855792,
        "course-id": 208786,
        "percent-started": 0,
        "memory-aggregate": {
          "difficulty-bucket": null,
          "last-study-time": null,
          "see-next-at": null,
          "total-study-time-millis": 0,
          "accuracy": 0,
          "level": 0.0,
          "presentations-count": 0,
          "average-review-interval": 0,
          "average-current-retention": 0,
          "average-easiness-modifier": 0,
          "studied-items-count": 0,
          "unstarted-items-count": 4,
          "eligible-items-count": 0,
          "percent-correct": 0.0,
          "score": 0.0,
          "progress": 0.0
        },
        "learn-messaging": {
          "primary-text": "Get started!",
          "image": "milestone_complete_any_started",
          "button-primary-text": "Let's do this!"
        }
      }
    }
  ],
  "links": {},
  "meta": {
    "total-pages": 1,
    "total-count": 1
  }
}
```

This endpoint retrieves the assignments in a course.

### HTTP Request

`GET https://partners.cerego.com/v3/courses/:id/assignments`

### Query Parameters

| Parameter | Description                                                                           |
| --------- | ------------------------------------------------------------------------------------- |
| user_id   | Specify a user id to retrieve data related to the user's progress in each assignment. |

### Assignment Object

### - Attributes

| Attribute | type    | Description                                                               |
| --------- | ------- | ------------------------------------------------------------------------- |
| name      | string  | The name of the assignment                                                |
| goal-type | integer | Specifies the type of assignment. Can be `set`, `assessment`, or `survey` |

### - Meta

| Attribute                 | type     | Description                                                             |
| ------------------------- | -------- | ----------------------------------------------------------------------- |
| assessment-score          | float    | The user's score on this assessment (`0.0` is 0%, `1.0` is 100%)        |
| memory-aggregate.progress | float    | The progress on this assignment (`0.0` is unstarted, `1.0` is complete) |
| last-study-time           | datetime | The time which the user last studied this assignment                    |

<!-- | assignment-available | boolean  | Returns true if the user is able to study/take the assignment. Could be false for a student if the assignment isn't published yet or if the student hasn't completed a prerequisite | -->
