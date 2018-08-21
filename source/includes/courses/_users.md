# Users

## Get all users in a course

```shell
curl https://cerego.com/api/v3/courses/:id/users
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1158898",
      "type": "users",
      "attributes": {
        "created-at": "2014-05-25T03:06:08.000Z",
        "name": "Abraham Lincoln",
        "username": "bowtoabe",
        "email": "bow.to.abe@example.com",
        "last-logged-in-at": "2017-12-14T18:55:14.000Z",
        "guid": "bff7431b-b099-4995-8b63-3b10a20223ab",
        "status": "courses.course_manager.members.studied_via_lti"
      },
      "relationships": {
        "user-partner-id": {
          "data": null
        }
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
  ],
  "meta": {
    "total-pages": 1,
    "total-count": 1
  }
}
```

This endpoint retrieves all users that are connected to a specific course.

### HTTP Request

`GET https://cerego.com/api/v3/courses/:id/users`

### User Object

Attribute | type | Description
--------- | --------- | -----------
created_at | datetime | When the user was created
name | string | The name of the user
username | string | The username of the user
email | string | The email of the user
last-logged-in-at | datetime | Time of last log in by the user
guid | string | An identifier for users that can be used across apps
status | string | `courses.course_manager.members.studied_via_lti` Student is connected to the course via LTI<br>`courses.course_manager.members.studied` Student has studied the course, but is not an LTI user<br>`courses.course_manager.members.invited` Student has received an invitation to join the course, but has not yet studied<br>`courses.course_manager.members.no_invitation_sent` No invitation has been sent to the user yet

### Meta

Attribute | type | Description
--------- | --------- | -----------
role | string | `learner` You are a student in the course <br>`instructor` You are teaching the course without permission to edit<br>`editor` Can edit: some content (only assigned sets and series)<br>`content_manager` Can manage (add/delete/edit): all content (sets and series)<br>`course_manager` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments<br>`admin` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments + organization level features and users
can-edit | boolean | The user is allowed to edit the current course
lti | boolean | The user has an LTI account connected
progress | float | The user's progress on this specific course (`0.0` is unstarted, `1.0` is complete)
percent-started | float | The percentage of concepts the user has started (`0.0` to `1.0`)
last-study-time | datetime | The time which the user last studied this course
payment-required | boolean | The user needs money to enable this course
cost | integer | Cost in cents to enable this course


## Add a user to a course

```shell
curl https://cerego.com/api/v3/courses/:id/users
    -d '{"email": "developers@cerego.com", "name": "Sarah Gough"}'
    -X POST
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> If you successfully make your POST request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "123460",
    "type": "users",
    "attributes": {
      "created-at": "2017-12-14T19:24:24.000Z",
      "name": "Julius Caesar",
      "username": "allhailtheromanempire@example.com",
      "email": "all.hail.the.roman.empire@example.com",
      "last-logged-in-at": null,
      "guid": "55d22545-92f2-40eb-9037-f9770c3516a9",
      "status": "courses.course_manager.members.invited"
    },
    "relationships": {
      "user-partner-id": {
        "data": null
      }
    },
    "meta": {
      "settings": {
        "notifications": {
          "daily-new-assignments": true
        }
      },
      "role": "student",
      "can-edit": false,
      "lti": false,
      "progress": 0,
      "percent-started": 0,
      "last-study-time": null,
      "payment-required": false,
      "cost": null
    }
  }
}
```

This endpoint adds a user to a course (or creates a new user if one does not exist)

### HTTP Request

`POST https://cerego.com/api/v3/courses/:id/users`

### Request Parameters

Parameter | Type | Required? | Description
--------- | --------- | --------- | -----------
email | string | yes | The email of the user you wish to add to the course
name | string | no | The name of the user you wish to add


<aside class="notice">If an account doesn't already exist, we will send them a welcome email with a link and instructions to set a password.</aside>

<aside class="warning">This endpoint is idempotent. (A user will not be added again if they are already in the course)</aside>

## Get a user in a course

```shell
curl https://cerego.com/api/v3/courses/:id/users/:id
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> If you successfully make your GET request you should receive a response that looks like this:

```json
{
  "data": {
    "id": "1849768",
    "type": "users",
    "attributes": {
      "created-at": "2017-12-14T19:24:24.000Z",
      "name": "Marie Antionette",
      "username": "cakeeaters",
      "email": "cake.eaters@example.com",
      "last-logged-in-at": "2017-12-14T20:33:31.000Z",
      "guid": "55d22545-92f2-40eb-9037-f9770c3516a9",
      "status": "courses.course_manager.members.invited"
    },
    "relationships": {
      "user-partner-id": {
        "data": null
      }
    },
    "meta": {
      "settings": {
        "notifications": {
          "daily-new-assignments": true
        }
      },
      "role": "student",
      "can-edit": false,
      "lti": false,
      "progress": 0,
      "percent-started": 0,
      "last-study-time": null,
      "payment-required": false,
      "cost": null
    }
  }
}
```

This endpoint gets information about a user within a course

### HTTP Request

`GET https://cerego.com/api/v3/courses/:id/users/:id`

## Remove a user from a course

```shell
curl https://cerego.com/api/v3/courses/:id/users/:id
    -X DELETE
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> If you successfully make your DELETE request you should receive a 204 No Content

This endpoint deletes a user from a course

### HTTP Request

`DELETE https://cerego.com/api/v3/courses/:id/users/:id`

<aside class="notice">Removing a user does NOT clear their memories or progress.</aside>

