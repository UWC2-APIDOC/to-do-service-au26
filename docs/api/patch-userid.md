---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: user resource
nav_order: 6
has_children: true
has_toc: false
# tags used by AI files
description: "Updating a User Email"
topic_type: reference
tags:
  - updating users
  - email
related_pages:
  - /get-user-by-id.md
api_endpoints:
  - "PATCH /users/{userid}"
version: "v1.0"
last_updated: "2026-11-22"
---

# Update a user email

| Property | Type | Description |
| --- | --- | --- |
| `firstName` | string | User's first name |
| `lastName` | string | User's last name |
| `email` | string | User's email address |

## Example request body

```json
{
  "email": "jenny.jones@example.com"
}
```

## Example successful request

HTTP status: 200 OK

```json
{
  "lastName": "Jones",
  "firstName": "Jenny",
  "email": "jenny.jones@example.com",
  "id": 5
}
```

## Authentication: required

Authentication requirements: HTTPS, valid email, and token

## Error Responses

| Status Code | Description |
| --- | --- |
| `400 Bad Request` | Invalid JSON, an empty request body, or unsupported properties. |
| `401 Unauthorized` | Authentication token is missing, invalid, or expired. |
| `403 Forbidden` | The requester does not have permission to modify the specified user. |
| `422 Unprocessible Content` | A recognized property fails validation |

Example error response:

Status code: 422 `Unprocessable Content`

```json
{
  "error": {
    "code": "INVALID_EMAIL",
    "message": "The email address format is invalid.",
    "field": "email"
  }
}
```
