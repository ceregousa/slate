# Introduction

> To test your connection to our API please use

```shell
curl https://partners.cerego.com/v3/my/profile \
    -H "Authorization: Bearer <API_KEY>"
```



Welcome to the Cerego API! You can use our API to access Cerego endpoints, which you can use to manage the users in your courses.

Our API follows the [JSON API](http://jsonapi.org/) standard. Please take note how objects within a certain resource are in the `included` section.

All endpoints will start with the following URL and follow standard RESTful practices.

`https://partners.cerego.com/v3/`

All requests should be made over SSL and it is recommend to use JSON to format your requests.

