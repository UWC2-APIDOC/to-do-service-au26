---
layout: default
title: "Tutorial: Create users and tasks with the To-Do Service API"
parent: Tutorials
nav_order: 4
description: "A first-use walkthrough for enrolling a user, retrieving a user by ID, posting users with curl, and adding a task."
topic_type: tutorial
tags:
  - api
  - quickstart
categories:
  - tutorial
ai_relevance: high
importance: 8
prerequisites:
  - /before-you-start-a-tutorial
related_pages:
  - /api/user
  - /api/task
  - /api/users-get-user-by-id
examples:
  - POST /users
  - GET /users/{id}
  - POST /tasks
api_endpoints:
  - POST /users
  - GET /users/{id}
  - POST /tasks
version: "v1.0"
last_updated: "2026-11-17"
---

# Tutorial: Create users and tasks with the To-Do Service API

Learn four common To-Do Service operations in one guided exercise:

1. [Enroll a new user](#1-enroll-a-new-user-postman).
2. [Get a user by ID](#2-get-a-user-by-id-postman).
3. [POST users](#3-post-users-terminal-example).
4. [Add a new task](#4-add-a-new-task-postman).

**Estimated time:** 20–25 minutes. **Audience:** First-time API users familiar with basic JSON.

By the end, you'll have created two users, retrieved one by ID, and added a task assigned to that user.

## Before you start

Follow [Before you start a tutorial](../before-you-start-a-tutorial.md) to install Node.js, `json-server` **0.17.4**, and the **Postman desktop app**, and to clone or fork the repository.

1. Open a terminal in the root of your local `to-do-service-au26` repository.
2. Start the API:

   ```bash
   cd api
   json-server -w to-do-db-source.json
   ```

   Leave this terminal open while you complete the tutorial. The default base URL is `http://localhost:3000`.

3. Check that the server responds. In a **second terminal**, run:

   ```bash
   curl http://localhost:3000/users
   ```

   **Expected result:** a JSON array of users (possibly empty), rather than a connection error.

4. In Postman, create an environment variable named `base_url` with the value `http://localhost:3000`. Select that environment. You can alternatively enter the full URL in every request.

> **Important:** User and task IDs depend on the contents of your local database. The IDs in this tutorial are examples, not guaranteed values. Save the IDs returned by your own requests.

## 1. Enroll a new user (Postman)

**Goal:** Add a user who can own tasks. **Endpoint:** `POST /users`.

1. Open Postman and create a new HTTP request.
2. Set the method to **POST** and the URL to `{{base_url}}/users`.
3. On the **Headers** tab, add `Content-Type` with value `application/json`.
4. On the **Body** tab, select **raw** and **JSON**, then enter:

   ```json
   {
     "firstName": "Alex",
     "lastName": "Rivera",
     "email": "alex.rivera@example.com"
   }
   ```

5. Select **Send**.

**Expected status:** `201 Created`. The response should include the properties you submitted and an automatically assigned `id`:

```json
{
  "firstName": "Alex",
  "lastName": "Rivera",
  "email": "alex.rivera@example.com",
  "id": 5
}
```

Your ID may be different. **Record the actual `id`**; you will use it in sections 2 and 4. In the examples below, `5` represents the ID returned by this request.

**Success check:** The response has your name and email, plus a new `id`.

## 2. Get a user by ID (Postman)

**Goal:** Confirm the new user can be retrieved. **Endpoint:** `GET /users/{id}`.

1. Create another request in Postman.
2. Set the method to **GET**.
3. Enter `{{base_url}}/users/5`, **replacing `5` with the user ID from section 1**.
4. Optionally add the header `Accept: application/json`.
5. Select **Send**. A GET request does not need a request body.

**Expected status:** `200 OK`. Example response:

```json
{
  "firstName": "Alex",
  "lastName": "Rivera",
  "email": "alex.rivera@example.com",
  "id": 5
}
```

**Success check:** The returned `id`, name, and email match the user created in section 1. A `404 Not Found` response usually means the ID does not exist in the current database.

## 3. POST users (terminal example)

**Goal:** Make a second `POST /users` request using `curl`, without Postman. This is the same API operation as enrollment, but demonstrates how to call it from a terminal.

1. In your second terminal, run:

   ```bash
   curl -i -X POST "http://localhost:3000/users" \
     -H "Content-Type: application/json" \
     -d '{
       "firstName": "Taylor",
       "lastName": "Chen",
       "email": "taylor.chen@example.com"
     }'
   ```

2. Look for **`HTTP/1.1 201 Created`** in the response headers (or an equivalent HTTP/1.1 status line) and a JSON object resembling:

   ```json
   {
     "firstName": "Taylor",
     "lastName": "Chen",
     "email": "taylor.chen@example.com",
     "id": 6
   }
   ```

3. Verify the second user with `GET /users/{id}` using the **actual** new ID. For example, if the server returned `6`:

   ```bash
   curl http://localhost:3000/users/6
   ```

**Success check:** Both the POST response and the follow-up GET show Taylor's details. If you run the POST again, it creates another record with a different ID.

## 4. Add a new task (Postman)

**Goal:** Assign a task to Alex, the user created in section 1. **Endpoint:** `POST /tasks`.

1. Create another request in Postman.
2. Set the method to **POST** and URL to `{{base_url}}/tasks`.
3. Add the header `Content-Type: application/json`.
4. On **Body > raw > JSON**, enter the following. **Replace `5` with Alex's actual user ID from section 1.**

   ```json
   {
     "userId": 5,
     "title": "Prepare weekly report",
     "description": "Collect project updates and submit the summary",
     "dueDate": "2026-12-01T17:00",
     "warning": 30
   }
   ```

   The properties `userId`, `title`, `description`, `dueDate`, and `warning` follow the [task resource definition](../api/task.md). `warning` represents minutes before the due date. Note the camel-case spelling **`dueDate`**, not `due_date`.

5. Select **Send**.

**Expected status:** `201 Created`. Example response:

```json
{
  "userId": 5,
  "title": "Prepare weekly report",
  "description": "Collect project updates and submit the summary",
  "dueDate": "2026-12-01T17:00",
  "warning": 30,
  "id": 5
}
```

**Success check:** The response contains a task `id` and a `userId` matching Alex's ID. Your task ID may differ from the example. To inspect the saved task, request `GET {{base_url}}/tasks/<task-id>` with the actual task ID returned; this is a standard `json-server` read operation.

## Troubleshooting

| Problem | Likely cause | What to do |
| --- | --- | --- |
| `ECONNREFUSED` or “Could not send request” | Server is not running or wrong port | Return to the first terminal, run `json-server -w to-do-db-source.json` from `api`, and confirm port `3000` |
| `404 Not Found` for `GET /users/{id}` | Incorrect or nonexistent user ID | Copy the `id` from the actual POST response; don't reuse the sample ID blindly |
| `404 Not Found` for `/users` or `/tasks` | Incorrect base URL or database file | Check that the URL uses `http://localhost:3000` and that the server loaded `to-do-db-source.json` |
| `400 Bad Request` or parsing error | Invalid JSON | Check commas, double quotes, and **Body > raw > JSON** |
| POST works but task belongs to the wrong user | Wrong `userId` in the task body | Use the ID returned when you enrolled Alex |
| New records disappear after resetting files | Local database was overwritten or restored | Re-run the POST request and use the newly returned IDs |

## What you learned

You can now use three API endpoints to complete four first-use workflows:

| Workflow | Method | Endpoint | Outcome |
| --- | --- | --- | --- |
| Enroll a new user | `POST` | `/users` | Creates a user through Postman |
| Get user by ID | `GET` | `/users/{id}` | Retrieves a specific user |
| POST users | `POST` | `/users` | Creates a user through `curl` |
| Add a new task | `POST` | `/tasks` | Creates a task assigned to a user |

## Related documentation

- [Before you start a tutorial](../before-you-start-a-tutorial.md)
- [Enroll a new user](enroll-a-new-user.md)
- [Add a new task](add-a-new-task.md)
- [POST users tutorial](post_users.md)
- [User resource](../api/user.md)
- [Get a user by ID API reference](../api/users-get-user-by-id.md)
- [Task resource](../api/task.md)

> **Note:** This tutorial uses the local `json-server` sample API, which writes to the local JSON database. Its behavior is for learning and testing; do not treat it as production authentication or user enrollment.
