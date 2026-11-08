---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: task resource
nav_order: 2
# tags used by AI files
description: GET a `task` resource by its ID from the service
topic_type: reference
tags:
    - api
categories:
    - api-reference
ai_relevance: high
importance: 7
prerequisites:
    - /api/task
related_pages: []
examples:
    - GET /tasks/{taskId}
test:
    test_apps:
        - json-server@0.17.4
    server_url: localhost:3000
    local_database: /api/to-do-db-source-test.json
    testable:
        - GET example
api_endpoints: 
    - /tasks/{taskId}
version: "v1.0"
last_updated: "2026-11-08"
# vale  on
# markdownlint-enable
---

# Get task by ID

Returns the [`task`](task.md) object that has the `id` specified by the `taskId` path parameter.

[Jump to examples](#examples)

## Endpoint

```shell
{server_url}/tasks/{taskId}
```

## Parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| `taskId` | number | Yes | The `id` of the task to return |

## Request headers

| Header | Value | Required |
| ------ | ----- | -------- |
| `Accept` | `application/json` | No |

## Request body

None

## Response body

```json
{
    "userId": 1,
    "title": "Grocery shopping",
    "description": "eggs, bacon, gummy bears",
    "dueDate": "2025-09-20T17:00",
    "warning": "10",
    "id": 1
}
```

## Examples

### `GET` example request

```bash
curl -G -H "Accept: application/json" \
    --url "http://localhost:3000/tasks/1"
```

#### `GET` example response

```json
{
    "userId": 1,
    "title": "Grocery shopping",
    "description": "eggs, bacon, gummy bears",
    "dueDate": "2025-09-20T17:00",
    "warning": "10",
    "id": 1
}
```

## Response status

| HTTP status value | Description |
| ------------- | ----------- |
| 200 | **Success:** Requested data returned successfully |
| 404 | **Not found:** No task has the specified `taskId`. The response body is `{}`. |
| ECONNREFUSED | Service is offline. Start, or restart the service and try again. |
