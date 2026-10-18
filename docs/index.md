---
layout: default
nav_order: 1
title: To-Do Service API
description: Start using the sample To-Do Service REST API, explore its resources, and find tutorials and API reference documentation.
topic_type: overview
tags:
  - introduction
  - api
categories:
  - overview
ai_relevance: high
importance: 9
prerequisites: []
related_pages:
  - /before-you-start-a-tutorial
  - /tutorials/add-a-new-task
  - /tutorials/enroll-a-new-user
examples: []
api_endpoints:
  - GET /users
  - GET /tasks
version: "v1.0"
last_updated: "2026-11-15"
---

# To-Do Service API

**Learn, experiment, and document a REST API for managing people and their tasks.**

The To-Do Service is an **instructional mock API**. It models how an application
could store users, assign tasks, and track due dates. Use it to practice HTTP
requests, JSON data, API reference writing, and technical documentation workflows.

[Get started](#quickstart){: .btn .btn-primary }
[Explore API resources](#api-resources){: .btn }
[Browse tutorials](#tutorials-and-guides){: .btn }

> **Important:** This is a sample service, not a production task-management platform.
> You run the mock API on your own computer. The published documentation site
> does not host a live API or send task reminders.

## At a glance

| Topic | Details |
|:--|:--|
| **Purpose** | Practice REST operations and writing documentation |
| **API style** | REST-like HTTP endpoints with JSON request and response bodies |
| **Local base URL** | `http://localhost:3000` |
| **Resources** | `users` and `tasks` |
| **Mock server** | `json-server` version `0.17.4` |
| **Starting data** | `api/to-do-db-source.json` |
| **Recommended clients** | Terminal with cURL or the Postman desktop app |
| **Documentation** | Markdown, Jekyll, and Just the Docs on GitHub Pages |

## What can you do with the API?

The project provides example data and a local mock HTTP server. You can:

- **Inspect users.** Retrieve user records that include a name, email address,
  and unique ID.
- **Inspect tasks.** Retrieve task records with an owner, title, description,
  due date, and warning interval.
- **Experiment with requests.** Use `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`
  supported by the local `json-server` mock server.
- **Practice API documentation.** Follow tutorials, examine resource properties,
  and contribute changes through GitHub.

**What the sample does not implement:** User sign-in, authentication, access
control, real email or push notifications, a cloud-hosted API backend, or
production-grade validation. A `warning` field represents reminder-related
sample data; it does **not** trigger a delivered alert.

## How the service works

```text
Your HTTP client (cURL or Postman)
                |
                | HTTP request to localhost:3000
                v
       json-server mock API
                |
                | Reads and updates JSON records
                v
       api/to-do-db-source.json
                |
                v
       JSON response to your client
```

The **documentation website** and the **mock API** have different roles.
GitHub Pages publishes the instructions you are reading. Your local
`json-server` process handles API requests. Opening the documentation
website alone does not start the API server.

## Quickstart

Follow these steps to make your first successful request.

### 1. Prepare your computer

Install [Git](https://git-scm.com/downloads) and a current supported
[Node.js](https://nodejs.org/en/download) release. You will also need a copy
of the [project repository](https://github.com/UWC2-APIDOC/to-do-service-au26).

In a terminal, verify that Node.js and npm are available:

```bash
node --version
npm --version
```

### 2. Clone the repository

Run the following command if you do not already have the repository locally:

```bash
git clone https://github.com/UWC2-APIDOC/to-do-service-au26.git
cd to-do-service-au26
```

If you already cloned **your fork**, open that local folder instead.
From the repository root, check that the sample data file exists:

```bash
ls api/to-do-db-source.json
```

### 3. Install the compatible mock server

The course materials use a specific `json-server` version:

```bash
npm install --global json-server@0.17.4
```

If your system reports an npm permission error, follow the
[npm permissions guidance](https://docs.npmjs.com/resolving-eacces-permissions-errors)
instead of automatically rerunning the install with `sudo`.

### 4. Start the API

From the **repository root**, run:

```bash
json-server --watch api/to-do-db-source.json --port 3000
```

Keep this terminal open. The default base URL is:

```text
http://localhost:3000
```

> **Tip:** `localhost` refers to your computer. It is not the GitHub Pages URL.
> If port 3000 is occupied, stop the conflicting process or use another port
> and update the URLs in your requests.

### 5. Make your first request

Open a **second terminal** and retrieve the first user:

```bash
curl http://localhost:3000/users/1
```

With the original sample database, the response is:

```json
{
  "lastName": "Smith",
  "firstName": "Ferdinand",
  "email": "f.smith@example.com",
  "id": 1
}
```

The response is a **JSON object**. It identifies one sample user. To retrieve
all users, use `GET /users`:

```bash
curl http://localhost:3000/users
```

To retrieve all tasks, use `GET /tasks`:

```bash
curl http://localhost:3000/tasks
```

**Success check:** If you receive JSON instead of a connection error, the
local API is responding.

## API resources

The starter database has two top-level collections.

### Users

A user represents someone who owns tasks.

**Collection endpoint:** `GET /users`  
**Single record:** `GET /users/{id}`

Example user:

```json
{
  "lastName": "Smith",
  "firstName": "Ferdinand",
  "email": "f.smith@example.com",
  "id": 1
}
```

| Field | Sample type | Meaning |
|:--|:--|:--|
| `id` | Number | Unique user record identifier |
| `firstName` | String | User's given name |
| `lastName` | String | User's family name |
| `email` | String | User's example email address |

[Read the user resource reference](api/user.md){: .btn }

### Tasks

A task represents an item associated with a user.

**Collection endpoint:** `GET /tasks`  
**Single record:** `GET /tasks/{id}`

Example task from the sample database:

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

| Field | Sample type | Meaning |
|:--|:--|:--|
| `id` | Number | Unique task record identifier |
| `userId` | Number | ID of the user associated with the task |
| `title` | String | Short name of the task |
| `description` | String | Longer explanation of the task |
| `dueDate` | String | Date and time without a time-zone offset in the sample |
| `warning` | String | Reminder interval in minutes, stored as text in the sample |

**Data-format note:** The sample JSON stores `warning` as a **string** (for
example, `"10"`). The existing task reference describes it as a number.
When creating examples, distinguish the format actually present in the starter
database from an intended schema. The existing add-task tutorial also uses
`due_date`, while the starter database uses `dueDate`; the example above uses
the database field name. Sample due dates omit a time-zone offset, so do not
assume they represent a specific global instant.

[Read the task resource reference](api/task.md){: .btn }

### Available operations in the mock server

The following operations reflect the installed `json-server` mock server.
They do not guarantee that every operation has a finished, dedicated page in
this documentation set.

| Method | Endpoint | Typical purpose |
|:--|:--|:--|
| `GET` | `/users` | List users |
| `GET` | `/users/{id}` | Retrieve one user |
| `POST` | `/users` | Create a user |
| `PUT` / `PATCH` | `/users/{id}` | Replace or update a user |
| `DELETE` | `/users/{id}` | Remove a user |
| `GET` | `/tasks` | List tasks |
| `GET` | `/tasks/{id}` | Retrieve one task |
| `GET` | `/tasks?userId=1` | Filter tasks for one user |
| `POST` | `/tasks` | Create a task |
| `PUT` / `PATCH` | `/tasks/{id}` | Replace or update a task |
| `DELETE` | `/tasks/{id}` | Remove a task |

**Note:** This mock server supports CRUD-style operations, but it does not
enforce application rules such as checking whether `userId` exists before
creating a task. You must not treat it as a secure production API.

## Request and response essentials

An HTTP request has a **method**, a **URL**, and optionally **headers** and a
**body**. An HTTP response returns a **status code**, headers, and often JSON.

| Concept | What it means in this project |
|:--|:--|
| Base URL | Location of your locally running API, usually `http://localhost:3000` |
| Endpoint | Resource path, such as `/tasks` |
| HTTP method | Operation such as `GET` or `POST` |
| Request header | Metadata, such as `Content-Type: application/json` |
| Request body | JSON sent to create or change a record |
| Response status | Outcome such as `200 OK`, `201 Created`, or `404 Not Found` |
| JSON | Text format used for structured resource data |

### Example: Create a task

First, ensure the mock server is running. Then send this request to create a
new task for the sample user with ID `1`:

```bash
curl --request POST http://localhost:3000/tasks \
  --header "Content-Type: application/json" \
  --data '{
    "userId": 1,
    "title": "Review API documentation",
    "description": "Check examples and links",
    "dueDate": "2026-12-01T17:00",
    "warning": "30"
  }'
```

The mock server generally responds with **201 Created** and a JSON record
that includes a generated `id`. The ID depends on the database's current
state, so don't assume it will be a particular number.

> **Caution:** With `--watch`, the local server writes changes to its database
> file. Use a disposable copy or restore the starter data before repeating
> examples that create, edit, or delete records.

### Example: Inspect HTTP status and headers

Use `--include` to see response headers and the status line:

```bash
curl --include http://localhost:3000/tasks/1
```

A successful request for an existing record ordinarily returns `200 OK`.
A request for a missing record ordinarily returns `404 Not Found`.

## Tutorials and guides

Choose a guide based on what you want to accomplish.

| Goal | Recommended page |
|:--|:--|
| Set up the local tools and database | [Before you start a tutorial](before-you-start-a-tutorial.md) |
| Create a user | [Enroll a new user](tutorials/enroll-a-new-user.md) |
| Add a task | [Add a new task](tutorials/add-a-new-task.md) |
| Understand user data | [User resource](api/user.md) |
| Understand task data | [Task resource](api/task.md) |
| Review contribution standards | [Documentation requirements](contributors-guide/documentation-requirements.md) |
| Follow writing conventions | [Writer's guide](contributors-guide/writers-guide.md) |

Some repository pages cover individual requests in more detail, and some
planned tutorials may be unfinished. Consult the navigation menu to see the
currently published pages.

## Troubleshooting

### `curl: (7) Failed to connect to localhost port 3000`

The API process is probably not running or is listening on a different port.
Start `json-server` in the first terminal and keep it open. Then repeat the
request from the second terminal.

### `json-server: command not found`

Confirm that the package was installed and that npm's global executable
folder is on your shell's `PATH`. You can also check npm installation and
permission errors using the official npm documentation.

### `No such file or directory` for the database

Make sure your terminal is in the repository root before running the startup
command. Use `pwd` to identify your current folder and `ls api` to confirm
the API database exists.

### A request returns `404 Not Found`

Check the path and record ID. For example, `/users/1` is a different route
from `/user/1`. A record may also have been deleted or never created.

### The JSON differs from the examples

Your local database may have changed after earlier `POST`, `PUT`, `PATCH`, or
`DELETE` requests. Compare it with `api/to-do-db-source.json` in the original
repository before assuming the documentation is wrong.

### The docs website works, but API requests fail

That is possible: the documentation is hosted online, but the API must be
started locally. The GitHub Pages site is not an API server.

## Contribute to the documentation

This project supports learning documentation-as-code: contributors edit
Markdown, validate content, and submit pull requests for review.

1. Fork the [original repository](https://github.com/UWC2-APIDOC/to-do-service-au26)
   and clone your fork.
2. Create a feature branch for your documentation changes.
3. Edit Markdown files in `docs/` using VS Code or another text editor.
4. Review the [documentation requirements](contributors-guide/documentation-requirements.md)
   and [writer's guide](contributors-guide/writers-guide.md).
5. Check formatting, examples, and navigation links before committing.
6. Push your branch and open a pull request.

The course repository's pull request workflow checks documentation formatting,
front matter, selected API examples, and commit structure. A passing preview
is not a substitute for reviewing technical correctness and usability.

For the project source, see the
[GitHub repository](https://github.com/UWC2-APIDOC/to-do-service-au26).

## Limitations and project scope

This project is for **education and experimentation**. It is not a deployed
commercial service, and the sample data is not intended for real personal
information. The included task dates are examples, not current schedules.

The source code and documentation are distributed under the
[MIT license](https://github.com/UWC2-APIDOC/to-do-service-au26/blob/main/LICENSE).

