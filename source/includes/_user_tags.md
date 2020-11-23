# User Tags

## About user tags

User tags can be used to assign custom tag values to a user. Smart Groups can then use these tags to automatically enroll users into courses based on the tag values. 

For example, you might set up a "Country" tag type for your account and then for each user set it to their country of residence. Then you could set up smart groups to automatically enroll users in the United States in one course, and users in Canada in a different course.  

## Set a user's tags

```shell
curl https://partners.cerego.com/v3/users/:userid/partner_user_tags \
    -d '{ 
          "tags": [{"partner_user_tag_type_id": "5", "value": "California"}, 
                   {"partner_user_tag_type_id": "9", "value": "Marketing"}] 
        }' \
    -X POST \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <API_KEY>"
```


This endpoint allows you to set tag values for a user. When using this you specify an array of objects, each object having a `partner_user_tag_type_id` and a `value` that should be set for that tag type. 

Tag types must be set up for your account ahead of time. Contact your customer support representative to know the ids for your account's tag types.   

### HTTP Request

`POST https://partners.cerego.com/v3/users/:userid/partner_user_tags`

### Request Parameters

Parameter | Type | Required? | Description
--------- | --------- | --------- | -----------
tags | array | yes | An array of objects. Each object should have a `partner_user_tag_type_id` and a `value`. For example, if your account has a tag type of "Country" which has an ID of "12" and also a tag type of "Employee ID" which has an ID of "13" then you could set both of them with: <br> [{"partner_user_tag_type_id": "12", "value": "United States"}, {"partner_user_tag_type_id": "13", "value": "B893247"}] 


 
