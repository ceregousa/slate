---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='https://cerego.com/'>Check out the Cerego website</a>

includes:
  - errors

search: true
---

# Introduction

> To test your connection to our API please use

```ruby

```

```shell
curl https://cerego.com/api/echo 
    -d '{"echo":"Test"}' 
    -X POST 
    -H "Content-Type: application/json"
```

```javascript

```

> Please note that all other endpoints require authentication via a Bearer Token.

Welcome to the Cerego API! You can use our API to access Cerego endpoints, which can get information on about courses, assignments, users, and more.

All V3 endpoints follow the [JSON API](http://jsonapi.org/) standard. Please take note how objects within a certain resource are in the includes section and -'s are used to denote spaces.

Cerego provides 3 different environments, 2 for testing and QA, as well as our primary production environment

`https://cerego.com/` - Production <br>
`https://stable.cerego.com/` - Stable (Used for QA) <br>
`https://testing.cerego.com/` - Testing (Used for heavy testing and unreleased features)

All 3 environments support our full range of APIs and will require all requests to be made over SSL. It is recommend to use JSON for all requests.

<aside class="notice">Testing and Stable use an anonymized version of the production database that is synced once per week.</aside>

<aside class="warning">Any changes made on Stable or Testing will be cleared away weekly on saturday.</aside>

# Authentication

Cerego utilizes the concept of bearer tokens to authenticate API calls. 

To easily acquire your bearer token please log into your [Cerego](https://cerego.com/) account (that has permission for the calls you wish to make) and then right click and press inspect. Please then click the tab that says console and then type in 

`Smartfm.API.token` 

![Acquire Token](/images/acquireToken.png)

You should see a string similar to 

`cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U` 

This is your Bearer token that you will need to use for API calls.

Cerego expects for Bearer token to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U`

<aside class="notice">
You must replace <code>cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U</code> with your personal Bearer token.
</aside>

<aside class="warning">Cerego does NOT currently use OAuth2. It is not possible to perform API calls on an individual user level.</aside>

# Courses

## Get all courses

```ruby
require 'oauth'

api = Oauth::APIClient.authorize!('your_token')
api.courses.get
```

```shell
curl https://cerego.com/api/v3/courses
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript
const request = require("request");
const url = "https://cerego.com/api/v3/courses";
request.get(url, (error, response, body) => {
  let json = JSON.parse(body);
  console.log(json);
});
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "13421",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T04:10:32.000Z",
        "name": "Introduction to Learning and Behavior : 9781305953079",
        "description": null,
        "slug": "introduction-to-learning-and-behavior-9781305953079-6321ba48-6df3-42b2-bf15-3001977b1110",
        "users-count": 3,
        "admin-users-count": 1,
        "student-users-count": 2,
        "goal-list-count": 0,
        "goals-count": 12,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Inst04 Mt"
        ],
        "ic-items-count": 0,
        "assignments-count": 12,
        "external-id": "367392"
      },
      "relationships": {
        "partner": {
          "data": {
            "id": "10",
            "type": "partners"
          }
        },
        "image": {
          "data": {
            "id": "865877",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/introduction-to-learning-and-behavior-9781305953079-6321ba48-6df3-42b2-bf15-3001977b1110"
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
      "id": "13422",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T06:01:10.000Z",
        "name": "Statistics for the Behavioral Sciences : 9781305647305",
        "description": null,
        "slug": "statistics-for-the-behavioral-sciences-9781305647305-ecce4b8e-433d-4e43-a58b-5eda6b6da2db",
        "users-count": 2,
        "admin-users-count": 1,
        "student-users-count": 1,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Stephanie Tobin"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "367413"
      },
      "relationships": {
        "partner": {
          "data": {
            "id": "10",
            "type": "partners"
          }
        },
        "image": {
          "data": null
        }
      },
      "links": {
        "self": "/v3/courses/statistics-for-the-behavioral-sciences-9781305647305-ecce4b8e-433d-4e43-a58b-5eda6b6da2db"
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
      "id": "865877",
      "type": "images",
      "attributes": {
        "created-at": "2016-04-04T22:06:29.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/865877/d59fa10pv0.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/865877"
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
filter[role] | `student` will display all courses that the user id is learning <br> `instructor` will diplay all courses the user id is teaching
filter[state] | `published` will display all courses that are in a published state <br> `unpublished` will display all courses that have not yet been published <br> `archived` will display all courses that have been archived
page[number] | Courses are paginated, use this to choose which page you want
page[size] | The default is `15` - How many courses are listed in each request/page
tab | `published` will display all courses that are in a published state <br> `unpublished` will display all courses that have not yet been published <br> `archived` will display all courses that have been archived
sort | Orders the results based on the param. <br>Example: `name` - sort in alphabetical order


### Course Object

Parameter | type | Description
--------- | --------- | -----------
created_at | datetime | When the course was created
name | string | The name of the course
description | string | The description of the course
slug | string | Unique name for the course
users-count | integer | The amount of users in the course
admin-users-count | integer | The amount of admins (instructors) in the course
student-users-count | integer | The amount of students in the course
goal-list-count | integer | The amount of series in the course
goals-count | integer | The amount of sets in the course
reports-count | integer | The amount of reports a set has
state | string | `published` Course is viewable <br> `unpublished` Course is hidden <br> `archived` Course is no longer in use
state-updated-at | datetime | Time of last time state was changed
instructor-names | array[string] | A list of instructor names for the course
ic-items-count | integer | The amount of instructional items in the course
assignments-count | integer | The amount of sets and series in course
external-id | integer | The LTI user associated with the course?

### Meta

Parameter | type | Description
--------- | --------- | -----------
settings | object | `daily-new-assignments` boolean<br>`signup-nudges` boolean<br>`daily-new-students` boolean<br>`daily-goals-reached` boolean<br>`weekly-stale-invitations` boolean
role | string | `learner` You are a student in the course <br>`instructor` You are teaching the course without permission to edit<br>`editor` You have permission to edit this specific content<br>`content_manager` You have permission to edit all content<br>`course_manager` You have permission to manage to entire course<br>`admin` You have permission to edit everything
can-edit | boolean | Determines if you are allowed to edit this content
progress | float | Your progress on this specific course (`0.0` is unstarted, `1.0` is complete)
percent-started | float | The percentage of concepts you have started (`0.0` to `1.0`)
last-study-time | datetime | The time which you last studied this course
payment-required | boolean | You owe money to enable this course
cost | integer | Cost in cents for to enable the course

## Get a course

```ruby

```

```shell
curl https://cerego.com/api/v3/courses/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript

```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "38410",
    "type": "courses",
    "attributes": {
      "created-at": "2017-11-27T09:52:52.000Z",
      "name": "Elsevier Adaptive Learning for Structure and Function of the Body, 14th Edition : 153260_nkane19_1001",
      "description": null,
      "slug": "elsevier-adaptive-learning-for-structure-and-function-of-the-body-14th-edition-153260_nkane19_1001",
      "users-count": 1,
      "admin-users-count": 1,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 1,
      "reports-count": 0,
      "state": "published",
      "state-updated-at": null,
      "instructor-names": [
        "Nerea Kane"
      ],
      "ic-items-count": 0,
      "assignments-count": 1,
      "external-id": "17431949894"
    },
    "relationships": {
      "partner": {
        "data": {
          "id": "4",
          "type": "partners"
        }
      },
      "image": {
        "data": {
          "id": "628253",
          "type": "images"
        }
      }
    },
    "links": {
      "self": "/v3/courses/elsevier-adaptive-learning-for-structure-and-function-of-the-body-14th-edition-153260_nkane19_1001"
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
      "id": "628253",
      "type": "images",
      "attributes": {
        "created-at": "2014-05-22T13:39:34.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/628253/61dvdt9c6hmi3o.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/628253"
      }
    }
  ]
}
```

This endpoint retrieves a course.

### HTTP Request

`GET https://cerego.com/api/v3/courses/:id`

## Create a course

```ruby

```

```shell
curl https://cerego.com/api/v3/courses
    -d '{"name": "Course Name", "description": "The Description of the Course", "partner_id": 21, "slug": "course-name"}'
    -X POST
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript

```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "38411",
    "type": "courses",
    "attributes": {
      "created-at": "2017-12-14T00:25:58.000Z",
      "name": "Course Name",
      "description": "The Description of the Course",
      "slug": "course-name",
      "users-count": 1,
      "admin-users-count": 0,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 0,
      "reports-count": 0,
      "state": "unpublished",
      "state-updated-at": null,
      "instructor-names": [
        "Kyle Stewart"
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
      "self": "/v3/courses/course-name"
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

```ruby

```

```shell
curl https://cerego.com/api/v3/courses/:id
    -d '{"name": "Updated Name", "description": "Updated Description", "slug": "updated-name", "state": "published"}'
    -X PUT
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript

```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "38414",
    "type": "courses",
    "attributes": {
      "created-at": "2017-12-14T00:30:26.000Z",
      "name": "New Name",
      "description": "Updated Description",
      "slug": "updated-name",
      "users-count": 1,
      "admin-users-count": 1,
      "student-users-count": 0,
      "goal-list-count": 0,
      "goals-count": 0,
      "reports-count": 0,
      "state": "published",
      "state-updated-at": null,
      "instructor-names": [
        "Kyle Stewart"
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
      "self": "/v3/courses/updated-name"
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

```ruby

```

```shell
curl https://cerego.com/api/v3/courses/:id
    -X DELETE
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript

```

> If you successfully make your DELETE request you should receive a 204 No Content

This endpoint deletes a course

### HTTP Request

`DELETE https://cerego.com/api/v3/courses/:id`

<aside class="warning">A course must be <code>unpublished</code> or <code>archived</code> to be deleted.</aside>

# Images

## Get an image

```ruby
```

```shell
curl https://cerego.com/api/v3/images/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer cDPuiaEQrttyDpGU8a1aJtltFUDJY9W31Hi/K+SY9c2WuqHio3dBVtBjagLxyh6U"
```

```javascript
```

```json
{
  "data": {
    "id": "662672",
    "type": "images",
    "attributes": {
      "created-at": "2014-08-19T17:17:24.000Z",
      "url": "https://assets.testing.cerego.com/uploads/image/uploader/662672/61evfr7fsl2aco.jpg",
      "orig-url": null,
      "orig-owner": null,
      "license-id": null,
      "alt-tag": null
    },
    "links": {
      "self": "/v3/images/662672"
    }
  }
}
```

This endpoint retrieves an image.

### HTTP Request

`GET https://cerego.com/api/v3/images/:id`

### Image Object

Parameter | Type | Description
--------- | ------- | -----------
created_at | datetime | The time which the image was created
url | string | The url for the image
orig-url | string | Link to where the url was if it was downloaded by an external resource
orig-owner | string | The name of the person who originally created the image if exported externally
license-id | integer | The id for the type of license on the image
alt-tag | string | The alt message when you hover over the image