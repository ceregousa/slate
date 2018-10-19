# Iframe Messages 

Cerego posts messages detailing information about the current user's study session and progress.

Messages are posted to the `window.parent` if inside an iframe, otherwise they are posted to the `window.opener`.

Cerego posts the following messages:

messageType | Scenario
---------- | -------
load-module | The user has loaded the assignment before or after a study session
next-quiz | The user has progressed inside a study session
end-session | The user has successfully completed a study session

To view the posted messages in your window you can use:

```window.addEventListener("message", function(event) { console.log(JSON.parse(event.data)); }, false);```


## Load Module

```json
{
  "messageType": "load-module",
  "context": {
    "type": "set",
    "id": 749831,
    "name": "Greek and Roman Gods"
  },
  "data": {
    "progress": 85,
    "studiedItemsCount": 14,
    "totalStudyTime": 245071,
    "itemsCount": 15
  }
}
```

When an assignment is launched from LTI or studied directly on Cerego.com, the assignment loads and presents the user with a summary screen.

The following parameters are sent in the `load-module` message:

Parameter | Description
---------- | -------
type | "set" or "series" depending on how the assignment is grouped
id | Set or Series id within Cerego
name | Name of the assignment
progress | The learner's progress to the goal, or 0 if no goal has been created
studiedItemsCount | How many items the learner has studied so far
totalStudyTime | Milliseconds spent in study sessions for this assignment
itemsCount | Total number of items in the assignment

## Next Quiz

```json
{ 
  "messageType": "next-quiz",
  "data": {
    "quizProgress": 33,
    "quizSize": 25
  }
}
```

Cerego posts a message when the learner progresses through a study session.

The following parameters are sent in the `next-quiz` message:

Parameter | Description
---------- | -------
quizProgress | progress 0-100 through the study session
quizSize | Number of total quiz screens. May increase on wrong answers.

## End Session

```json
{ 
  "messageType": "end-session",
  "data": {
    "quizProgress": 100,
    "quizSize": 25
  }
}
```

On successful completion of the study session, Cerego posts the `end-session message`:

Parameter | Description
---------- | -------
quizProgress | 100
quizSize | Number of total quiz screens viewed
