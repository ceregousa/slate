# Introduction

> To test your connection to our API please use

```shell
curl https://cerego.com/api/echo 
    -d '{"echo":"Test"}' 
    -X POST 
    -H "Content-Type: application/json"
```

```json
{
  "meta": {
    "status": 200,
    "message": "OK"
  },
  "response": {
    "echo": null
  }
}
```

> Please note that all other endpoints require authentication via a Bearer Token.

Welcome to the Cerego API! You can use our API to access Cerego endpoints, which you can use to get information on courses, assignments, users, and more.

All V3 endpoints follow the [JSON API](http://jsonapi.org/) standard. Please take note how objects within a certain resource are in the includes section and parameters are dasherized.

All V3 endpoints will start with the following URL and follow standard RESTful practices.

`https://cerego.com/api/v3/`

All requests should be made over SSL and it is recommend to use JSON to format your requests.

