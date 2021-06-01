# Users

## Get all users in a course

```shell
curl https://partners.cerego.com/v3/courses/:id/users \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
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

`GET https://partners.cerego.com/v3/courses/:id/users`

### User Object

| Attribute         | type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ----------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| created_at        | datetime | When the user was created                                                                                                                                                                                                                                                                                                                                                                                                    |
| name              | string   | The name of the user                                                                                                                                                                                                                                                                                                                                                                                                         |
| username          | string   | The username of the user                                                                                                                                                                                                                                                                                                                                                                                                     |
| email             | string   | The email of the user                                                                                                                                                                                                                                                                                                                                                                                                        |
| last-logged-in-at | datetime | Time of last log in by the user                                                                                                                                                                                                                                                                                                                                                                                              |
| guid              | string   | An identifier for users that can be used across apps                                                                                                                                                                                                                                                                                                                                                                         |
| status            | string   | `courses.course_manager.members.studied_via_lti` Student is connected to the course via LTI<br>`courses.course_manager.members.studied` Student has studied the course, but is not an LTI user<br>`courses.course_manager.members.invited` Student has received an invitation to join the course, but has not yet studied<br>`courses.course_manager.members.no_invitation_sent` No invitation has been sent to the user yet |

### Meta

| Attribute        | type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| role             | string   | `learner` You are a student in the course <br>`instructor` You are teaching the course without permission to edit<br>`editor` Can edit: some content (only assigned sets and series)<br>`content_manager` Can manage (add/delete/edit): all content (sets and series)<br>`course_manager` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments<br>`admin` Can manage (add/delete/edit): all content (sets and series) + all courses and assignments + organization level features and users |
| can-edit         | boolean  | The user is allowed to edit the current course                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| lti              | boolean  | The user has an LTI account connected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| progress         | float    | The user's progress on this specific course (`0.0` is unstarted, `1.0` is complete)                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| percent-started  | float    | The percentage of concepts the user has started (`0.0` to `1.0`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| last-study-time  | datetime | The time which the user last studied this course                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| payment-required | boolean  | The user needs money to enable this course                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| cost             | integer  | Cost in cents to enable this course                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## Add a user to a course

```shell
curl https://partners.cerego.com/v3/courses/:id/users \
    -d '{"email": "developers@cerego.com", "name": "Sarah Gough"}' \
    -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
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

`POST https://partners.cerego.com/v3/courses/:id/users`

### Request Parameters

| Parameter | Type   | Required? | Description                                                                                                                                                                                                                                     |
| --------- | ------ | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| email     | string | no        | The email of the user you wish to add to the course. Required unless you specify member_id.                                                                                                                                                     |
| member_id | string | no        | The member ID of the user you wish to add to the course. A member ID is a unique and unchanging identifier for the user that you have, for example an employee ID. If you specify this, then you must also specify name, and not specify email. |
| name      | string | no        | The name of the user you wish to add                                                                                                                                                                                                            |

<aside class="notice">If an account doesn't already exist, we will send them a welcome email with a link and instructions to set a password.</aside>

<aside class="warning">This endpoint is idempotent. (A user will not be added again if they are already in the course)</aside>

## Get a user in a course

```shell
curl https://partners.cerego.com/v3/courses/:id/users/:id \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
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

`GET https://partners.cerego.com/v3/courses/:id/users/:id`

## Remove a user from a course

```shell
curl https://partners.cerego.com/v3/courses/:id/users/:id \
    -X DELETE \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your DELETE request you should receive a 204 No Content

This endpoint deletes a user from a course

### HTTP Request

`DELETE https://partners.cerego.com/v3/courses/:id/users/:id`

<aside class="notice">Removing a user does NOT clear their memories or progress.</aside>

## Get users in a partner

This endpoint retrieves users in a partner.

```shell
curl GET https://partners.cerego.com/v3/partners/:partner_id/users?query=:member_id&include_enrolled_courses=true\
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
```

> If you successfully make your GET request you should receive a response that looks like this:

```json
{
    "data": [
        {
            "id": "1234567",
            "type": "users",
            "attributes": {
                "created-at": "2020-10-16T00:24:54.000Z",
                "name": "name",
                "username": "username",
                "email": null,
                "last-logged-in-at": null,
                "guid": "f105f8e0-122b-479d-98c7-97as65869de7a",
                "has-password": false,
                "course-stats": [
                    {
                        "id": 4639,
                        "title": "Useful References",
                        "progress": 0.0,
                        "total-study-time-millis": 0,
                        "last-study-time": null,
                        "assignments-data": []
                    },
                    {
                        "id": 10175,
                        "title": "Sales Demo",
                        "progress": 0.0,
                        "total-study-time-millis": 0,
                        "last-study-time": null,
                        "assignments-data": [
                            {
                                "id": 762921,
                                "name": "CHAPTER 1: The Scientific Study of Life",
                                "total-study-time-millis": 0,
                                "last-study-time": null,
                                "score": 0.0
                            },
                            {
                                "id": 762925,
                                "name": "UNIT 1: The Cellular Basis of Life",
                                "total-study-time-millis": 0,
                                "last-study-time": null,
                                "score": 0.0
                            }
                    }
                ]
            },
            "relationships": {
                "image": {
                    "data": null
                },
                "emails": {
                    "data": []
                },
                "user-partner-id": {
                  "data": null
                },
                "partner-user-tags": {
                    "data": []
                }
            },
            "meta": {
                "role": null,
                "can-edit-partner": false,
                "can-create-course": false,
                "can-edit-course": false,
                "can-create-content": false,
                "can-manage-content": false,
                "can-read-content": false,
                "can-edit-content": false,
                "can-manage-learners": false
            }
        }
    ],
    "meta": {
        "total-pages": 1,
        "total-count": 1
    }
}
```

### HTTP Request

`GET https://partners.cerego.com/v3/partners/:partner_id/users`

### Query Parameters

| Parameter                | Description                                                                                                          |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| query                    | Specify a query if you are looking for a single user. The value should be either the member_id or email of the user. |
| include_department_users | If specified, users in departments of the partner will also be included.                                             |
| include_enrolled_courses | If set to true, each user will have a "course-stats" attribute containing progress and study information.            |
| page[number]             | Results are paginated, use this to choose which page you want                                                        |
