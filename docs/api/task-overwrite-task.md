---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: task resource
nav_order: 3
# tags used by AI files
description: "PUT data in an existing task"
tags: 
    - api
categories: 
    - api-reference
ai_relevance: high
importance: 7
prerequisites: "/api/task"
related_pages: 
    - /tutorials/add-a-new-task
    - /tutorials/task
examples: "PUT /tasks/{{taskID}}"
api_endpoints:
    /tasks
version: "v1.0"
last_updated: 2026-11-07
# vale  on
# markdownlint-enable
---

# `PUT` or overwrite a task by ID

<!-- vale write-good = NO -->
<!-- vale Google.Passive = NO -->
<!-- vale Google.Headings = NO -->
<!-- vale Google.Parens = NO -->
<!-- vale Google.Acronyms = NO -->

Returns an overwritten array of task data reflecting
the changes in the `PUT` request for the task
specified with the `taskId`.

Endpoint:

```shell
{{server_url}}/tasks/{{taskId}}
```

Contains information about tasks stored for the users of the service.

There must be an existing task in the service, with
a user associated with it. Learn more about the
[user resource](user.md).

## Parameters

| Parameter name | Type | Description |
| ------------- | ----------- | ----------- |
| `taskId` | number | The ID number of the task resource |

## Request headers

| Header | Value | Description |
| ------------- | ----------- | ----------- |
| `Content-Type` | `application/JSON` | Tells the server you are sending data in JSON format. |

## Request example

```bash
curl -X PUT http://{{server_url}}/tasks/{{taskId}} \
     -H "Content-Type: application/json" \
     -d '{
          "userid": 1,
          "title": "Kroger",
          "description": "milk, sugar, flour",
          "dueDate": "2026-11-07T17:00",
          "warning": "10",
          "id": 1
         }'
```

## Response example

```bash
{
  "userid": 1,
  "title": "Kroger",
  "description": "milk, sugar, flour",
  "dueDate": "2026-11-07T17:00",
  "warning": "10",
  "id": 1
}
```

<!-- markdownlint-disable MD013 -->

| Property name | Type | Description |
| ------------- | ----------- | ----------- |
| `userId` | number | The ID of the user resource to which this task is assigned |
| `title` | string | The title or short description of the task |
| `description` | string | The long description of the task |
| `dueDate` | string | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)format of the date and time the task is due |
| `warning` | number | Minutes before the `dueDate`. Must be a positive integer. |
| `id` | number | The task's unique record ID, or `taskID` |

## Response status

| HTTP status value | Description |
| ------------- | ----------- |
| 200 | **Success**: requested data returned successfully |
| 404 | **Error**: specified user record not found |
| ECONNREFUSED | Service is offline. Start, or restart the service and try again. |

<!-- markdownlint-enable MD013 -->

## Related topics

<!-- vale Vale.Terms = NO -->

* [Tasks API Reference](../api/task.md)
* [Add a New Task Tutorial](../tutorials/add-a-new-task.md)
