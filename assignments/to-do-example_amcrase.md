---
# markdownlint-disable
# vale off

layout: default
description: The To-Do Service is a REST API for managing tasks and user information.
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

# To-Do Service

<!-- vale Google.Acronyms = off -->

**Author:** `Aly Crase`

The To-Do Service is a REST API for managing tasks and user information related to those tasks.

## curl examples

This section shows how to call the To-Do Service with curl. In the examples, `{server_url}`
stands for the host and port where the service is running. For example, when you run the
service locally, `{server_url}` is `localhost:3000`.

### `GET` example (curl)

The `GET` request retrieves a single user by ID. It returns the user's first name, last name,
email address, and ID.

#### `GET` example request (curl)

```bash
curl http://{server_url}/users/1
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

The `POST` request creates a new user. The request body includes the user's first name,
last name, and email address. The service returns the new user record, including its
assigned ID.

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

This section shows how to call the To-Do Service with Postman. In the examples,
`{server_url}` stands for the host and port where the service is running. For example,
when you run the service locally, `{server_url}` is `localhost:3000`.

### `GET` example (Postman)

The `GET` request retrieves a single user by ID. It returns the user's first name, last
name, email address, and ID.

#### `GET` example request (Postman)

```bash
http://localhost:3000/users/1
```

#### `GET` example response (Postman)

```json
{
  "lastName": "Smith",
  "firstName": "Ferdinand",
  "email": "f.smith@example.com",
  "id": 1
}
```

### `POST` example (Postman)

The `POST` request creates a new user. The request body includes the user's first name,
last name, and email address. The service returns the new user record, and includes its
assigned ID.

#### `POST` example request (Postman)

```bash
http://localhost:3000/users
```

##### `POST` request headers (Postman)

```text
Content-Type: application/json
```

##### `POST` request data (Postman)

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com"
}
```

#### `POST` example response (Postman)

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "id": 5
}
```
