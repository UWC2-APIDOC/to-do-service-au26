---
# markdownlint-disable
# vale off
layout: default
description: <REPLACE with description of this API endpoint>
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

# Assignment 5.3

<!-- vale Google.Acronyms = off -->

**Author:** `Sharvil Gupta`

{REPLACE WITH a brief description of what this endpoint does.}

## curl examples

{REPLACE WITH an overview of this section. Be sure to explain what {server_url} means if you use it.}

### `GET` example (curl)

{The GET request retrieves the user whose ID is 1 from the /users resource. If that user exists, the server returns a 200 OK status and a JSON object containing the user's information.}

#### `GET` example request (curl)

```bash
curl http://localhost:3000/users/1
```

#### `GET` example response (curl)

```json
[
  {
    "lastName": "Smith",
    "firstName": "Ferdinand",
    "email": "f.smith@example.com",
    "id": 1
  },
```

### `POST` example (curl)

{The POST request sends a JSON object containing a new user's first name, last name, and email address to the /users endpoint.}

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
{{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "id": 7
}}
```

## Postman examples

{## Postman examples

This section demonstrates how to use Postman to send GET and POST requests to the To-Do Service API and examine the JSON responses. The GET request retrieves existing user information, while the POST request creates a new user in the database.

The `{server_url}` placeholder represents the base URL of the API server.}

### `GET` example (Postman)

{The GET request uses Postman to retrieve an existing user from the To-Do Service API. The request is sent to the `/users/1` endpoint at `http://localhost:3000/users/1`. If successful, the server returns an HTTP **200 OK** status code and a JSON object containing the user's ID, first name, last name, and email address. Unlike a POST request, a GET request retrieves information without creating or modifying data.}

#### `GET` example request (Postman)

```bash
{Rhttp://localhost:3000/users/1}
```

#### `GET` example response (Postman)

```json
{lastName	Smith
firstName	Ferdinand
email	f.smith@example.com
id	1}
```

### `POST` example (Postman)

{The POST request uses Postman to create a new user in the To-Do Service database. The request sends a JSON object containing the user's first name, last name, and email address to the `/users` endpoint at `http://localhost:3000/users`. If successful, the server adds the new user to the database and returns an HTTP **201 Created** status code, along with a JSON response containing the user's information and a unique ID assigned by the server.}

#### `POST` example request (Postman)

```bash
{
  curl -X POST http://{server_url}/users \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com"
  }'

}
```

##### `POST` request headers (Postman)

```text
{
X-Powered-By Express 
Vary Origin, Accept-Encoding
Access-Control-Allow-Credentials true
Cache-Control no-cache
Pragma no-cache
Expires -1
X-Content-Type-Options nosniff
Content-Type application/json; 
charset=utf-8 Content-Length
98 Etag W/"62-7ZVLmu4Y1DoKejs7Q1BR3SVfj/s" 
Date Sat, 07 Nov 2026 01:31:38 GMT
Connection keep-alive
Keep-Alive timeout=5
}
```

##### `POST` request data (Postman)

```json
{{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com"
}}
```

#### `POST` example response (Postman)

```json
{{
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com",
    "id": 9
}}
```
