---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Cerego API! You can use our API to access Cerego API endpoints, which can get information on about courses, assignments, users, and more.

For all V3 endpoints Cerego follows the [JSON API](http://jsonapi.org/) standard.

We have language bindings in Shell, Ruby, and Javascript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const cerego = require('cerego');

let api = cerego.authorize('token123');
```

> Make sure to replace `token123` with your API key.

Cerego uses OAuth to allow access to the API. You can create an OAuth Client by going to the [Partner Page](https://cerego.com/partners/21/oauth)

Click "Add OAuth Client" at the top right of the page, include the name of your organization, and click Create

Cerego expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer token123`

<aside class="notice">
You must replace <code>token123</code> with your personal API key.
</aside>

# Courses

## Get all courses

```ruby
require 'oauth'

api = Oauth::APIClient.authorize!('your_token')
api.courses.get
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const request = require("request");
const url = "https://www.cerego.com/api/v3/courses";
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
    },
    {
      "id": "13429",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T15:47:01.000Z",
        "name": "Statistics for the Behavioral Sciences : 9781305647305",
        "description": null,
        "slug": "statistics-for-the-behavioral-sciences-9781305647305-81e80601-3d11-4047-80f0-f0f68cb991b8",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 2,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Diana Sulewski"
        ],
        "ic-items-count": 0,
        "assignments-count": 2,
        "external-id": "367719"
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
        "self": "/v3/courses/statistics-for-the-behavioral-sciences-9781305647305-81e80601-3d11-4047-80f0-f0f68cb991b8"
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
      "id": "13432",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T16:37:54.000Z",
        "name": "Statistics for the Behavioral Sciences : 9781305858329",
        "description": null,
        "slug": "statistics-for-the-behavioral-sciences-9781305858329-a17f95e7-f761-4db7-a61f-2e7e6ca7b8d4",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Kathleen Schmidt"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "367762"
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
        "self": "/v3/courses/statistics-for-the-behavioral-sciences-9781305858329-a17f95e7-f761-4db7-a61f-2e7e6ca7b8d4"
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
      "id": "13436",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T18:51:14.000Z",
        "name": "Elsevier Adaptive Learning for Adult Health Nursing, 7th Edition : 153778_densmingerstokes_1001",
        "description": null,
        "slug": "elsevier-adaptive-learning-for-adult-health-nursing-7th-edition-153778-densminge",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Dawn EnsmingerStokes"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "13988809556"
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
            "id": "676333",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/elsevier-adaptive-learning-for-adult-health-nursing-7th-edition-153778-densminge"
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
      "id": "13438",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T19:02:03.000Z",
        "name": "Childhood and Adolescence: Voyages in Development : 9781305864337",
        "description": null,
        "slug": "childhood-and-adolescence-voyages-in-development-9781305864337-0335292e-4d3f-4824-b881-68b90d28add2",
        "users-count": 8,
        "admin-users-count": 1,
        "student-users-count": 7,
        "goal-list-count": 0,
        "goals-count": 6,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "KATHRYN Kotowski"
        ],
        "ic-items-count": 0,
        "assignments-count": 6,
        "external-id": "318230"
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
            "id": "859507",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/childhood-and-adolescence-voyages-in-development-9781305864337-0335292e-4d3f-4824-b881-68b90d28add2"
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
      "id": "13440",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T20:33:19.000Z",
        "name": "Elsevier Adaptive Learning for Mosby's Essential Sciences for Therapeutic Massage, 4th Edition : 153780_tyttri_1001",
        "description": null,
        "slug": "elsevier-adaptive-learning-for-mosby-s-essential-sciences-for-therapeutic-massag-ea1ee9b7-f8a9-4085-aa0d-47766b2cc9be",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Tiffany Yttri"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "13988497583"
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
            "id": "662672",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/elsevier-adaptive-learning-for-mosby-s-essential-sciences-for-therapeutic-massag-ea1ee9b7-f8a9-4085-aa0d-47766b2cc9be"
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
      "id": "13441",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T20:39:52.000Z",
        "name": "Research Methods for the Behavioral Sciences : 9781305264939",
        "description": null,
        "slug": "research-methods-for-the-behavioral-sciences-9781305264939-3ac9607d-452e-4a31-9045-f938f54f660e",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Tralise J Legg"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "368063"
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
            "id": "902999",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/research-methods-for-the-behavioral-sciences-9781305264939-3ac9607d-452e-4a31-9045-f938f54f660e"
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
      "id": "13442",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T20:39:55.000Z",
        "name": "Research Methods for the Behavioral Sciences : 9781305264939",
        "description": null,
        "slug": "research-methods-for-the-behavioral-sciences-9781305264939-4be98eb0-71fe-469a-993c-daf0a94bf657",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Logan Yelderman"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "368069"
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
            "id": "902999",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/research-methods-for-the-behavioral-sciences-9781305264939-4be98eb0-71fe-469a-993c-daf0a94bf657"
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
      "id": "13447",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-26T22:47:29.000Z",
        "name": "Cognitive Psychology : 9781337100052",
        "description": null,
        "slug": "cognitive-psychology-9781337100052-5d1adb6a-a087-452d-99d2-b90ae3b247a2",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "James Finlay"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "368127"
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
            "id": "957776",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/cognitive-psychology-9781337100052-5d1adb6a-a087-452d-99d2-b90ae3b247a2"
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
      "id": "13452",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-27T04:59:57.000Z",
        "name": "Statistics for the Behavioral Sciences : 9781305647305",
        "description": null,
        "slug": "statistics-for-the-behavioral-sciences-9781305647305-e23aee10-4dbb-45f0-8636-dcaacf537cec",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Lauren Merrill"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "308869"
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
        "self": "/v3/courses/statistics-for-the-behavioral-sciences-9781305647305-e23aee10-4dbb-45f0-8636-dcaacf537cec"
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
      "id": "13453",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-27T05:17:50.000Z",
        "name": "Discovering Psychology: : 9781305097650",
        "description": null,
        "slug": "discovering-psychology-9781305097650-afc76b15-ac31-414d-bb9a-3a4cc993602b",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Jill Meyers-Welch"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "368190"
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
            "id": "711768",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/discovering-psychology-9781305097650-afc76b15-ac31-414d-bb9a-3a4cc993602b"
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
      "id": "13454",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-27T05:35:17.000Z",
        "name": "Biblemesh Living Faith Bible College-NT-LFBC: (Fall 2016)-New Testament Survey",
        "description": null,
        "slug": "biblemesh-living-faith-bible-college-nt-lfbc-fall-2016-new-testament-survey",
        "users-count": 3,
        "admin-users-count": 2,
        "student-users-count": 1,
        "goal-list-count": 4,
        "goals-count": 18,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Dennis Traverse",
          "Dennis Traverse"
        ],
        "ic-items-count": 0,
        "assignments-count": 22,
        "external-id": "group-2466"
      },
      "relationships": {
        "partner": {
          "data": {
            "id": "13",
            "type": "partners"
          }
        },
        "image": {
          "data": {
            "id": "805626",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/biblemesh-living-faith-bible-college-nt-lfbc-fall-2016-new-testament-survey"
      },
      "meta": {
        "settings": null,
        "role": "instructor",
        "can-edit": true,
        "lti": false,
        "progress": null,
        "percent-started": null,
        "last-study-time": null,
        "payment-required": null,
        "cost": null
      }
    },
    {
      "id": "13462",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-27T15:10:04.000Z",
        "name": "Elsevier Adaptive Learning for Fundamentals of Nursing, 1st Edition : 154642_pellis30_1002",
        "description": null,
        "slug": "elsevier-adaptive-learning-for-fundamentals-of-nursing-1st-edition-154642-pellis-c644c65b-2300-46ac-a234-c8c9c2eec362",
        "users-count": 108,
        "admin-users-count": 6,
        "student-users-count": 102,
        "goal-list-count": 0,
        "goals-count": 44,
        "reports-count": 55,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Mary Krieger",
          "Michelle Whittenberg",
          "Melodie Wong",
          "Gail Ellis",
          "Laura Riedel",
          "Wyble Kerri"
        ],
        "ic-items-count": 0,
        "assignments-count": 44,
        "external-id": "13857546460"
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
            "id": "693616",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/elsevier-adaptive-learning-for-fundamentals-of-nursing-1st-edition-154642-pellis-c644c65b-2300-46ac-a234-c8c9c2eec362"
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
      "id": "13464",
      "type": "courses",
      "attributes": {
        "created-at": "2016-07-27T15:23:37.000Z",
        "name": "Elsevier Adaptive Learning for The Language of Medicine, 11th Edition : 156516_vhodges15_1001",
        "description": null,
        "slug": "elsevier-adaptive-learning-for-the-language-of-medicine-11th-edition-156516-vhod",
        "users-count": 1,
        "admin-users-count": 1,
        "student-users-count": 0,
        "goal-list-count": 0,
        "goals-count": 1,
        "reports-count": 0,
        "state": "published",
        "state-updated-at": null,
        "instructor-names": [
          "Veronica Hodges"
        ],
        "ic-items-count": 0,
        "assignments-count": 1,
        "external-id": "13945057490"
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
            "id": "774248",
            "type": "images"
          }
        }
      },
      "links": {
        "self": "/v3/courses/elsevier-adaptive-learning-for-the-language-of-medicine-11th-edition-156516-vhod"
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
    },
    {
      "id": "676333",
      "type": "images",
      "attributes": {
        "created-at": "2014-10-28T12:24:58.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/676333/b14v1palp9bk80.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/676333"
      }
    },
    {
      "id": "859507",
      "type": "images",
      "attributes": {
        "created-at": "2016-03-25T17:49:14.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/859507/331df8brns.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/859507"
      }
    },
    {
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
    },
    {
      "id": "902999",
      "type": "images",
      "attributes": {
        "created-at": "2016-05-23T22:37:47.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/902999/c29p800l9o.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/902999"
      }
    },
    {
      "id": "957776",
      "type": "images",
      "attributes": {
        "created-at": "2016-06-30T23:39:42.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/957776/1q0421590.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/957776"
      }
    },
    {
      "id": "711768",
      "type": "images",
      "attributes": {
        "created-at": "2015-04-23T18:53:40.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/711768/512vfuf96pefuc.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/711768"
      }
    },
    {
      "id": "805626",
      "type": "images",
      "attributes": {
        "created-at": "2015-11-08T18:53:10.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/805626/3369dpetfo.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/805626"
      }
    },
    {
      "id": "693616",
      "type": "images",
      "attributes": {
        "created-at": "2015-02-04T14:44:51.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/693616/a13v8negnvcafg.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/693616"
      }
    },
    {
      "id": "774248",
      "type": "images",
      "attributes": {
        "created-at": "2015-08-25T18:34:52.000Z",
        "url": "https://assets.testing.cerego.com/uploads/image/uploader/774248/517vev46mfoie4.jpg",
        "orig-url": null,
        "orig-owner": null,
        "license-id": null,
        "alt-tag": null
      },
      "links": {
        "self": "/v3/images/774248"
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

`GET https://www.cerego.com/api/v3/courses`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a course

```ruby
require 'oauth'

api = Oauth::APIClient.authorize!('your_token')
api.courses.get
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const request = require("request");
const url = "https://maps.googleapis.com/maps/api/geocode/json?address=Florence";
request.get(url, (error, response, body) => {
  let json = JSON.parse(body);
  console.log(json);
});
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

`GET https://www.cerego.com/api/v3/courses/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

