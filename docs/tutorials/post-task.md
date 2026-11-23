---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: Tutorials
nav_order: 1
# tags used by AI files
description: "Create a Task in the To-Do Server"
topic_type: tutorial
tags: 
    - api, task
categories: 
    - api-tutorial
ai_relevance: high
importance: 8
prerequisites:
    - /tutorials/add-a-new-task
    - /before-you-start-a-tutorial
related_pages: 
    - /tutorials/add-a-new-task
examples: POST /tasks
api_endpoints:
    - /tasks
version: "v1.0"
last_updated: "2026-11-22"
# vale  on
# markdownlint-enable
---

# Tutorial: Add a new `task` resource

<!-- vale write-good = NO -->
<!-- vale Google.Passive = NO -->
<!-- vale Google.Headings = NO -->
<!-- vale Google.Parens = NO -->
<!-- vale Google.Acronyms = NO -->

Base endpoint:

```shell
{to-do-service}/tasks
```

Contains information about tasks stored for the users of the service.

To have a task in the service, the user must be added to
the service first. Learn more about the [user resource](user.md).

## Resource properties

Sample `task` resource

```json

{
    "userId": 2,
    "title": "Pay bills",
    "description": "water, sewer, electric",
    "dueDate": "2026-011-24T12:00",
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
| `dueDate` | string | The [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format of the date and time the task is due |
| `warning` | number | The number of minutes before the `dueDate` to alert the user of the task. This must be a positive integer. |
| `id` | number | The task's unique record ID |

<!-- markdownlint-enable MD013 -->

## Procedure

### Send the Post request to the Server

1. In Postman, create a new POST request.
2. Enter the endpoint.
3. Add the following header: Content-Type: `application/json`

### Enter Task Information

1. From the body tab, select raw and choose JSON.
2. Enter the request in the body, like the below example:

    ```json
    {
        "title": "Pay bills",
        "description": "Pay monthly utility bills",
        "due_date": "2026-11-24"
    }
    ```

3. Click Send to submit POST request to the server.
4. Review the response. If the request succeeds, it may return an HTTP status 201.

## READ

<!-- vale Vale.Terms = NO -->

* [Get all tasks _(coming soon)_](#resource-properties)
* [Get task by ID _(coming soon)_](#resource-properties)
* [Get task by user ID _(coming soon)_](#resource-properties)
