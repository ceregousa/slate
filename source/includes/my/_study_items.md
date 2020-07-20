# My Study Items

## Get the current user's recommended study items

```shell
curl https://cerego.com/api/v3/my/study_items
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <API_KEY>"
```

> The above command returns JSON structured like this:

```json
{
	"data": [{
		"id": "4380603324461362534",
		"type": "study-items",
		"attributes": {
			"learning-engine-guid": "31b836b5-db1a-11e3-80a0-0ad95b10f3a0",
			"sequence": ["Study", "MultipleChoiceLimited", "ReverseMultipleChoiceLimited"]
		},
		"relationships": {
			"memory": {
				"data": null
			},
			"item": {
				"data": {
					"id": "164887",
					"type": "items"
				}
			},
			"collection": {
				"data": {
					"id": "723650",
					"type": "sets"
				}
			}
		}
	}, {
		"id": "103127985695213353",
		"type": "study-items",
		"attributes": {
			"learning-engine-guid": "2f8e6f00-db1a-11e3-80a0-0ad95b10f3a0",
			"sequence": ["Study", "MultipleChoiceLimited", "ReverseMultipleChoiceLimited"]
		},
		"relationships": {
			"memory": {
				"data": null
			},
			"item": {
				"data": {
					"id": "164893",
					"type": "items"
				}
			},
			"collection": {
				"data": {
					"id": "723650",
					"type": "sets"
				}
			}
		}
	}, {
		"id": "2996372568742862356",
		"type": "study-items",
		"attributes": {
			"learning-engine-guid": "2f8e6f91-db1a-11e3-80a0-0ad95b10f3a0",
			"sequence": ["Study", "MultipleChoiceLimited", "ReverseMultipleChoiceLimited"]
		},
		"relationships": {
			"memory": {
				"data": null
			},
			"item": {
				"data": {
					"id": "164897",
					"type": "items"
				}
			},
			"collection": {
				"data": {
					"id": "723650",
					"type": "sets"
				}
			}
		}
	}, {
		"id": "2499760633674352370",
		"type": "study-items",
		"attributes": {
			"learning-engine-guid": "31c9370c-db1a-11e3-80a0-0ad95b10f3a0",
			"sequence": ["MultipleChoiceLimited"]
		},
		"relationships": {
			"memory": {
				"data": {
					"id": "9072917",
					"type": "memory-estimates"
				}
			},
			"item": {
				"data": {
					"id": "177670",
					"type": "items"
				}
			},
			"collection": {
				"data": {
					"id": "728001",
					"type": "sets"
				}
			}
		}
	}],
	"meta": {
		"total-pages": null,
		"total-count": 22,
		"see-next-at": "2014-08-25T10:21:55.000Z",
		"eligible-items-count": 19,
		"unstarted-items-count": 3,
		"show-fading-tab": true,
		"body-text-html": "You'll \u003cb\u003ereview 19\u003c/b\u003e concepts from Chinese Core 1000: Step 3 [Simplified], Thầy Vinh Series and 2 other sets\u003cbr\u003e\u003cbr\u003eThis will take about 5 minutes.",
		"button-text": "Let's Review!",
		"study-session-id": "c7fbf38b-2f45-4986-9e59-ab6658d3ce92"
	}
}
```

This endpoint retrieves an array of study items representing a study session for the user.

### HTTP Request

`GET https://cerego.com/api/v3/my/study_items`

### Query Parameters

Parameter | Description
--------- | -----------
filter[status] | (fading or recommended) Fading returns only items that need review. Recommended returns only items that are unstarted or need review. If you don't provide this, it'll return a study session that even includes things that are good for now.
set_id | Return only study items from the specified set
series_id | Return only study items from the specified series
group_id | Return only study items from the specified course


### StudyItem Object

Attribute | type | Description
--------- | --------- | -----------
id | integer | This is a unique id for the study item. It doesn't correspond to anything and is randomly generated.
learning_engine_guid | string | This is the learning engine guid for the facet being studied. In the case of an instructional item which doesn't have a learning engine guid, it is a random string.
sequence | string[] | An array of quizzes that should be performed.


Relation | type | Description
--------- | --------- | -----------
memory | MemoryEstimate | The user's memory estimate for this item. Can be nil if the user hasn't studied it or it is an instructional item.
item | Item | The item that this StudyItem is indicating should be studied.
collection | Collection | The set or series that this item was picked from.


### Meta

Attribute | type | Description
--------- | --------- | -----------
total-pages | null | This endpoint is not paginated. It returns a good session size worth of study items.
total-count | integer | The number of study items
see-next-at | datetime | The earliest date at which an item from this context will become/became due
eligible-items-count | integer | The number of fading items that were returned
unstarted-items-count | integer | The number of unstarted items that were returned
body-text-html | string | A string that explains to the user what they will study
button-text | string | A string representing a call to action to get the user to study
study-session-id | string | A guid representing this entire set of study items. The study session will be temporarily saved on the back end. You can pass this guid to another study endpoint to say you want to study these study items.


