# Courses

## Get all courses

```shell
curl https://cerego.com/api/v3/courses
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "123456",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T04:10:32.000Z",
        "name": "Introduction to the Cerego API",
        "description": null,
        "slug": "introduction-to-the-cerego-api",
        "users-count": 3,
        "admin-users-count": 1,
        "student-users-count": 2,
        "goal-list-count": 0,
        "goals-count": 12,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Mr. Professor"
        ],
        "ic-items-count": 0,
        "assignments-count": 12,
        "external-id": "654321"
      },
      "relationships": {
        "partner": {
          "data": {
            "id": "21",
            "type": "partners"
          }
        },
        "image": {
          "data": {
            "id": "123456",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/introduction-to-the-cerego-api"
      },
      "meta": {
        "settings": null,
        "role": "instructor",
        "can-edit": true,
        "lti": true,
        "progress": null,
        "percent-started": null,
        "last-study-time": null,
        "payment-required": null,
        "cost": null
      }
    },
    {
      "id": "123457",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T06:01:10.000Z",
        "name": "The learning science behind the banana revolution",
        "description": null,
        "slug": "the-learning-science-behind-the-banana-revolution",
        "users-count": 2,
        "admin-users-count": 1,
        "student-users-count": 1,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Dr. Knowitall"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "666666"
      },
      "relationships": {
        "partner": {
          "data": {
            "id": "21",
            "type": "partners"
          }
        },
        "image": {
          "data": null
        }
      },
      "links": {
        "self": "/v3/courses/the-learning-science-behind-the-banana-revolution"
      },
      "meta": {
        "settings": null,
        "role": "instructor",
        "can-edit": true,
        "lti": true,
        "progress": null,
        "percent-started": null,
        "last-study-time": null,
        "payment-required": null,
        "cost": null
      }
    }
  ],
  "included": [
    {
      "id": "123456",
      "type": "images",
      "attributes": {
        "created-at": "2016-04-04T22:06:29.000Z",
        "url": "https://assets.cerego.com/uploads/image/uploader/123456/h3ll0m473.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/123456"
      }
    }
  ],
  "links": {
    "self": "http://localhost:3001/v3/courses?page%5Bnumber%5D=1&page%5Bsize%5D=15",
    "next": "http://localhost:3001/v3/courses?page%5Bnumber%5D=2&page%5Bsize%5D=15",
    "last": "http://localhost:3001/v3/courses?page%5Bnumber%5D=2510&page%5Bsize%5D=15"
  },
  "meta": {
    "total-pages": 2510,
    "total-count": 37641
  }
}
```

This endpoint retrieves all courses.

### HTTP Request

`GET https://cerego.com/api/v3/courses`

### Query Parameters

Parameter | Description
--------- | -----------
filter[partner_id] | Scopes the courses returned to the partner specified.
filter[role] | `student` will display all courses that the user is learning <br> `instructor` will display all courses the user is teaching
filter[state] | `published` will display all courses that are in a published state <br> `unpublished` will display all courses that have not yet been published <br> `archived` will display all courses that have been archived
page[number] | Courses are paginated, use this to choose which page you want
page[size] | The default is `15` - How many courses are listed in each request/page
tab | `published` will display all courses that are in a published state <br> `unpublished` will display all courses that have not yet been published <br> `archived` will display all courses that have been archived
sort | Orders the results based on the param. <br>Example: `name` - sort in alphabetical order


### Course Object

Attribute | type | Description
--------- | --------- | -----------
created_at | datetime | When the course was created
name | string | The name of the course
description | string | The description of the course
slug | string | Unique name for the course
users-count | integer | The number of users in the course
admin-users-count | integer | The number of admins (instructors) in the course
student-users-count | integer | The number of students in the course
goal-list-count | integer | The number of series in the course
goals-count | integer | The number of sets in the course
reports-count | integer | The number of reports a set has
state | string | `published` Course is viewable <br> `unpublished` Course is hidden <br> `archived` Course is no longer in use
state-updated-at | datetime | The most recent time that state was changed
instructor-names | array[string] | A list of instructor names for the course
ic-items-count | integer | The number of instructional items in the course
assignments-count | integer | The number of sets and series in course
external-id | integer | The LTI user associated with the course

### Meta

Attribute | type | Description
--------- | --------- | -----------
settings | object | `daily-new-assignments` boolean - Will receive notifications when new assignments become published<br>`signup-nudges` boolean - Will receive steps and advice on getting you set up<br>`daily-new-students` boolean - Will receive notifications about new students joining your courses<br>`daily-goals-reached` boolean - Will receive notifications when students reach an assigned goal<br>`weekly-stale-invitations` boolean - Will receive weekly summary of students who haven't confirmed their invitation
role | string | `learner` You are a student in the course <br>`instructor` You are teaching the course without permission to edit<br>`editor` Can edit: some content (only assigned sets and series)<br>`content_manager` Can manage (add/delete/edit): all content (sets and series)<br>`course_manager` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments<br>`admin` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments + organization level features and users
can-edit | boolean | Determines if you are allowed to edit this content
progress | float | Your progress on this specific course (`0.0` is unstarted, `1.0` is complete)
percent-started | float | The percentage of concepts you have started (`0.0` to `1.0`)
last-study-time | datetime | The time which you last studied this course
payment-required | boolean | You need to pay money to enable this course
cost | integer | Cost in cents to enable the course

## Get a course

```shell
curl https://cerego.com/api/v3/courses/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "123456",
    "type": "courses",
    "attributes": {
      "created-at": "2017-11-27T09:52:52.000Z",
      "name": "Introduction to the Cerego api",
      "description": null,
      "slug": "introduction-to-the-cerego-api",
      "users-count": 1,
      "admin-users-count": 1,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 1,
      "reports-count": 0,
      "state": "published",
      "state-updated-at": null,
      "instructor-names": [
        "Mr. Professor"
      ],
      "ic-items-count": 0,
      "assignments-count": 1,
      "external-id": "12345678"
    },
    "relationships": {
      "partner": {
        "data": {
          "id": "21",
          "type": "partners"
        }
      },
      "image": {
        "data": {
          "id": "123456",
          "type": "images"
        }
      }
    },
    "links": {
      "self": "/v3/courses/introduction-to-the-cerego-api"
    },
    "meta": {
      "settings": null,
      "role": "instructor",
      "can-edit": true,
      "lti": true,
      "progress": null,
      "percent-started": null,
      "last-study-time": null,
      "payment-required": null,
      "cost": null
    }
  },
  "included": [
    {
      "id": "123456",
      "type": "images",
      "attributes": {
        "created-at": "2014-05-22T13:39:34.000Z",
        "url": "https://assets.cerego.com/uploads/image/uploader/628253/h3ll0m473.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/123456"
      }
    }
  ]
}
```

This endpoint retrieves a course.

### HTTP Request

`GET https://cerego.com/api/v3/courses/:id`

## Create a course

```shell
curl https://cerego.com/api/v3/courses
    -d '{"name": "How To Achieve World Domination", "description": "The is pleasant course for those interested in conquering all life all on earth.", "partner_id": 21, "slug": "how-to-achieve-world-domination"}'
    -X POST
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "123458",
    "type": "courses",
    "attributes": {
      "created-at": "2017-12-14T00:25:58.000Z",
      "name": "How To Achieve World Domination",
      "description": "The is pleasant course for those interested in conquering all life all on earth.",
      "slug": "how-to-achieve-world-domination",
      "users-count": 1,
      "admin-users-count": 0,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 0,
      "reports-count": 0,
      "state": "unpublished",
      "state-updated-at": null,
      "instructor-names": [
        "Genghis Khan"
      ],
      "ic-items-count": null,
      "assignments-count": 0,
      "external-id": null
    },
    "relationships": {
      "partner": {
        "data": {
          "id": "21",
          "type": "partners"
        }
      },
      "image": {
        "data": null
      }
    },
    "links": {
      "self": "/v3/courses/how-to-achieve-world-domination"
    },
    "meta": {
      "settings": {
        "notifications": {
          "daily-new-assignments": true,
          "signup-nudges": true,
          "daily-new-students": true,
          "daily-goals-reached": true,
          "weekly-stale-invitations": true
        }
      },
      "role": "instructor",
      "can-edit": true,
      "lti": true,
      "progress": 0,
      "percent-started": 0,
      "last-study-time": null,
      "payment-required": false,
      "cost": null
    }
  }
}
```

This endpoint creates a new course

### HTTP Request

`POST https://cerego.com/api/v3/courses`

### Request Parameters

Parameter | Type | Required? | Description
--------- | --------- | --------- | -----------
name | string | yes | The name of the course
partner_id | integer | yes | The partner associated with this course
description | string | no | The description of the course
slug | string | no | The slug for the course

## Update a course

```shell
curl https://cerego.com/api/v3/courses/:id
    -d '{"name": "27 Title You Should not Use In API Documentation", "description": "A comprehensive list of every absurd title you can use for examples in your API documentation.", "slug": "27-titles-you-shouldnt-use-in-api-documentation", "state": "published"}'
    -X PUT
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "123459",
    "type": "courses",
    "attributes": {
      "created-at": "2017-12-14T00:30:26.000Z",
      "name": "27 Title You Should not Use In API Documentation",
      "description": "A comprehensive list of every absurd title you can use for examples in your API documentation.",
      "slug": "27-titles-you-shouldnt-use-in-api-documentation",
      "users-count": 1,
      "admin-users-count": 1,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 0,
      "reports-count": 0,
      "state": "published",
      "state-updated-at": null,
      "instructor-names": [
        "Ninja Wizard Developer"
      ],
      "ic-items-count": null,
      "assignments-count": 0,
      "external-id": null
    },
    "relationships": {
      "partner": {
        "data": {
          "id": "21",
          "type": "partners"
        }
      },
      "image": {
        "data": null
      }
    },
    "links": {
      "self": "/v3/courses/27-titles-you-shouldnt-use-in-api-documentation"
    },
    "meta": {
      "settings": {
        "notifications": {
          "daily-new-assignments": true,
          "signup-nudges": true,
          "daily-new-students": true,
          "daily-goals-reached": true,
          "weekly-stale-invitations": true
        }
      },
      "role": "instructor",
      "can-edit": true,
      "lti": true,
      "progress": 0,
      "percent-started": 0,
      "last-study-time": null,
      "payment-required": false,
      "cost": null
    }
  }
}
```

This endpoint updates an existing course

### HTTP Request

`PUT https://cerego.com/api/v3/courses/:id`

### Request Parameters

Parameter | Type | Description
--------- | --------- | -----------
name | string | The name of the course
state | string | `published` will display all courses that are in a published state <br> `unpublished` will display all courses that have not yet been published <br> `archived` will display all courses that have been archived
description | string | The description of the course
slug | string | The slug for the course

## Delete a course

```shell
curl https://cerego.com/api/v3/courses/:id
    -X DELETE
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your DELETE request you should receive a 204 No Content

This endpoint deletes a course

### HTTP Request

`DELETE https://cerego.com/api/v3/courses/:id`

<aside class="warning">A course must be <code>unpublished</code> or <code>archived</code> to be deleted.</aside>

