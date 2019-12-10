# Suggested Distractors

```shell
curl https://cerego.com/api/v4/suggested_distractors?question=Mars+is+a+_____+in+our+solar+system.&texts[]=planet
    -H "Content-Type: application/json"
    -H "Authorization: Bearer <BEARER_TOKEN>"
```

> The above commands return JSON structured like this:

```json
{
    "data": {
        "attributes": {
            "distractors": [
                {
                    "score": 0.5128877305160076,
                    "text": "comet"
                },
                {
                    "score": 0.44849844472922,
                    "text": "meteoroid"
                },
                {
                    "score": 0.4226289259750449,
                    "text": "asteroid"
                },
                {
                    "score": 0.40354014758008244,
                    "text": "nebula"
                },
                {
                    "score": 0.3826155365752833,
                    "text": "moon"
                },
                {
                    "score": 0.37483423014980904,
                    "text": "earth"
                },
                {
                    "score": 0.3670427768325058,
                    "text": "spaceship"
                },
                {
                    "score": 0.3667323313256961,
                    "text": "starship"
                },
                {
                    "score": 0.3226379576151075,
                    "text": "moonlet"
                },
                {
                    "score": 0.3176745914217421,
                    "text": "galaxy"
                }
            ]
        },
        "id": "planet",
        "type": "suggested-distractors"
    }
}
```

This endpoint retrieves suggested distractors (or, similar words) of `texts` based on the context of the `question`.

### HTTPS Request

`GET https://cerego.com/api/v4/suggested_distractors?question=Mars+is+a+_____+in+our+solar+system.&texts[]=planet`

### Query Parameters

Parameter | Description
--------- | -----------
question | The question context
texts | The texts, or correct answers, to distract

### Returned Distractor Objects

Attribute | type | Description
--------- | ---- | -----------
score | float | confidence of the distractor's relevance
text | string | the name of the distractor
