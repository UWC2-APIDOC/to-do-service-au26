---
layout: default
description: Learn what the To-Do Service API does and find tutorials and reference docs
topic_type: overview
nav_order: 1
related_pages:
  - Before you start a tutorial
  - "Tutorial: Enroll a new user"
  - "Tutorial: Add a new task"
---

# To-Do Service API

The To-Do Service API is a mock API. It simulates the REST interface of an imaginary service. You
can use it to learn how a REST API works and to practice writing API documentation.

The imaginary To-Do Service provides a cloud-hosted task list. Subscribers add new tasks and
receive reminders of those tasks.

This documentation is for developers who want to learn the API. Writers who want to improve the
documentation are welcome to. See [Contributing](https://uwc2-apidoc.github.io/to-do-service-au26/contributing/).

## Before you begin

To try the examples, review [Before you start a tutorial](https://uwc2-apidoc.github.io/to-do-service-au26/before-you-start-a-tutorial/)
to configure your development system.
It walks you through the full setup, including the GitHub and Git tools you need.

## Quickstart example

After your system is ready, start the service and send your first request.

In the `api` folder of your repository, run this command to start the service:

```bash
json-server -w to-do-db-source.json
```

The service starts at `http://localhost:3000`. In a second terminal, run this command to get the
user with ID 2:

```bash
curl http://localhost:3000/users/2
```

The service returns the user as JSON:

```json
{
    "lastName": "Jones",
    "firstName": "Jill",
    "email": "j.jones@example.com",
    "id": 2
}
```

## Tutorials

Learn how to do common tasks in the To-Do Service.

- [Enroll a new user](https://uwc2-apidoc.github.io/to-do-service-au26/tutorials/enroll-a-new-user/)
- [Add a new task](https://uwc2-apidoc.github.io/to-do-service-au26/tutorials/add-a-new-task/)
- [Add a new user](https://uwc2-apidoc.github.io/to-do-service-au26/tutorials/post_users/)
- [Get user by ID](https://uwc2-apidoc.github.io/to-do-service-au26/tutorials/get-user-by-id/)

### Planned tutorials

These tutorials are coming soon:

- Change the due date of a task
- Delete a task

## API reference docs

Detailed descriptions of the service's resources.

The service has two resources:

| Resource | What it holds | Methods |
| --- | --- | --- |
| `user` | The people who own tasks | GET, POST |
| `task` | The tasks assigned to users | GET, POST, PUT, DELETE |

Add a user before you add a task, because each task belongs to a user.

The API reference docs refer to a `{base_url}` when they refer to the URL of a resource. The
`{base_url}` value depends on the installation of the service.

When run locally for testing, the `{base_url}` is generally `http://localhost:3000`.

- [User resource](/to-do-service-au26/api/user/)
- [Task resource](/to-do-service-au26/api/task/)
