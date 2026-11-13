---
# markdownlint-disable
# vale off

layout: default
description: To-Do Service
topic_type: reference
# test:
#   test_apps:
#     - json-server@0.17.4
#   server_url: localhost:3000
#   local_database: /api/to-do-db-source.json
#   testable:
#     - GET example / 200
#     - POST example / 201
# vale  on
# markdownlint-enable
---

# To-do-service examples

<!-- vale Google.Acronyms = off -->

**Author:** `Ainsley Elder`

This endpoint allows you to retrieve, create, edit, and delete users and tasks.

## curl examples

This section provides examples of curl commands to retrieve and create
To-Do Service users.

### `GET` example (curl)

This request retrieves user information for the ID number specified in
the command from a local server. In this case, 1.

#### `GET` example request (curl)

```bash
curl http://localhost:3000/users/1
```

#### `GET` example response (curl)

```json
{
  "lastName": "Smith",
  "firstName": "Ferdinand",
  "email": "f.smith@example.com",
  "id": 1
}

```

### `POST` example (curl)

This request creates a user with the name and email specified
in the command at the specified server.

#### `POST` example request (curl)

```bash
curl -X POST http://{server_url}/users \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com"
  }'
```

#### `POST` example response (curl)

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "id": 5
}
```

## Postman examples

These examples use Postman to retrieve and create tasks from
the To-Do Service. In this case, the `base_url` root server
address is `http://localhost:3000` for a local server.

### `GET` example (Postman)

This request asks the local server for details for To-Do
Service task #1.

#### `GET` example request (Postman)

```bash
{base_url}/tasks/1
```

#### `GET` example response (Postman)

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

### `POST` example (Postman)

This request creates a new task on the server.

#### `POST` example request (Postman)

```bash
{base_url}/tasks
```

##### `POST` request headers (Postman)

| Key | Value |
| --- | --- |
| X-Powered-By | Express |
| Vary | Origin, X-HTTP-Method-Override, Accept-Encoding |
| Access-Control-Allow-Credentials | true |
| Cache-Control | no-cache |
| `Pragma` | no-cache |
| Expires | -1 |
| Access-Control-Expose-Headers | Location |
| Location | `http://localhost:3000/tasks/5` |
| X-Content-Type-Options | `nosniff` |
| Content-Type | `application`/json; charset=utf-8 |
| Content-Length | 161 |
| `Etag` | W/"a1-Z3Ss6DcfWmU+ksW/E3l6e5VZ/CA" |
| Date | Thu, 29 October, 2026 23:12:07 GMT |
| Connection | keep-alive |
| Keep-Alive | timeout=5 |

##### `POST` request data (Postman)

```json
{
    "task_title": "Get new tires",
    "task_description": "Get new tires for Hoppity",
    "task_due_date": "2025-03-11T14:00",
    "task_warning": "-60"
}
```

#### `POST` example response (Postman)

```json
{
    "task_title": "Get new tires",
    "task_description": "Get new tires for Hoppity",
    "task_due_date": "2025-03-11T14:00",
    "task_warning": "-60",
    "id": 5
}
```
