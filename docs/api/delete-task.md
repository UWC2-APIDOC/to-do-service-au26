---
layout: default
parent: task resource
description: Delete a task resource by its ID from the service
topic_type: reference
nav_order: 3
test:
  server_url: localhost:3000
  local_database: /api/to-do-db-source.json
  testable:
    - DELETE example
---

# Delete task by ID

Deletes the [`task`](./task.md) resource that has
the `id` specified by the `taskId` path parameter. After the service deletes the task, you can't
get the task by its ID.

[Jump to examples](#examples)

## Endpoint

```text
DELETE {server_url}/tasks/{taskId}
```

## Parameters

| Parameter | Type | Required | Description |
| --------- | ------ | -------- | ------------------------------ |
| `taskId` | number | Yes | The `id` of the task to delete |

## Request headers

None

## Request body

None

## Access requirements

The service doesn't require authentication. You don't need an API key or token to call this
operation.

## Response body

The response body is an empty JSON object.

```json
{}
```

## Examples

### `DELETE` example request

```bash
curl -X DELETE {server_url}/tasks/1
```

### `DELETE` example response

```json
{}
```

## Response status

| HTTP status value | Description |
| ----------------- | ------------------------------------------------------------------- |
| 200 | **Success:** the service deleted the task. |
| 404 | **Not found:** no task has the `taskId`. The response body is `{}`. |
| ECONNREFUSED | Service is offline. Start, or restart the service and try again. |
