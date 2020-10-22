# Courses

## Get courses

```shell
curl https://partners.cerego.com/api/v3/courses
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

This endpoint retrieves courses in a partner.

### HTTP Request

`GET https://cerego.com/api/v3/courses`

### Query Parameters

Parameter | Description
--------- | -----------
filter[partner_id] | Required. Scopes the courses returned to the partner specified.
user_id | Specify a user id to get the courses that the user is enrolled in as a student. Defaults to the currently signed in user
include_department_courses | If specified, courses in departments of `partner_id` that the user is enrolled in will also be returned
sort | Orders the results based on the param. <br>Example: `name` - sort in alphabetical order
page[number] | Courses are paginated, use this to choose which page you want


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
goals-count | integer | The number of sets in the course
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

