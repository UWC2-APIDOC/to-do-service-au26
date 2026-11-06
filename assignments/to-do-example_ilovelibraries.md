---
# markdownlint-disable
# vale off

layout: default
description: Retrieves and create users in a database.
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

# How to retrieve and create user data

<!-- vale Google.Acronyms = off -->

**Author:** `Rebecca Simms`

Retrieves user information with their id and creates new users.

## curl examples

This section shows examples of using curl in a command line interface to GET and POST user data. Replace {server_url} with the URL configured on your system.

### `GET` example (curl)

This GET example request retrieves user data for the user with the unique identifier 3.

#### `GET` example request (curl)

```bash
curl http://{server_url}/users/3
```

#### `GET` example response (curl)

```json
{
  "lastName": "Martinez",
  "firstName": "Marty",
  "email": "m.martinez@example.com",
  "id": 3
}
```

### `POST` example (curl)

This POST example updates the user database by creating the entry for user Jane Doe.

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
  "last_name": "Doe",
  "first_name": "Jane",
  "email": "jane.doe@example.com",
  "id": 6
}
```

## Postman examples

This section shows examples of using Postman to GET and POST user data. Replace {base_url} with the URL configured on your system.

### `GET` example (Postman)

This GET example request retrieves tasks for the user with the unique identifier 3.

#### `GET` example request (Postman)

```bash
{base_url}/tasks/3
```

#### `GET` example response (Postman)

```json
{
    "userId": 2,
    "title": "Oil change",
    "description": "5K auto service",
    "dueDate": "2025-11-10T09:00",
    "warning": "60",
    "id": 3
}
```

### `POST` example (Postman)

This POST example creates a task for a user.

#### `POST` example request (Postman)

```bash
{{base_url}}/tasks
```

##### `POST` request headers (Postman)

```text
Content-Type:application/json
```

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
