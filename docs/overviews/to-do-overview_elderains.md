---
# markdownlint-disable
# vale off

layout: default
description: To-Do Service Overview
topic_type: overview
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
The cloud-hosted tool for keeping to-do list current and tidy.

[**Start a Tutorial**](/docs/index.md#tutorials) |
[**API Reference**](/docs/index.md#api-reference-docs)

## Stay on task

With the To-Do Service, create a list of tasks, assign
them due dates, and set reminders.

## Keep others on task, too

Create users and allow them to create their own
task lists, or share tasks with others.

## Adding others to the service is easy

All you need to create a new user is a name
and email address.

### `POST` example in `curl`: create a new user

```bash
curl -X POST http://{server_url}/users \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "New",
    "lastName": "User",
    "email": "newuser@example.com"
  }'
```

[**Add your first user >**](/docs/tutorials/enroll-a-new-user.md)

## How can one use the to-do list?

### Keep your house in order

Homeowners have an unending list of things to do. Have the service
remind you to take out the trash, clear the gutters, check the
furnace filter, and more. Invite someone from your household to
share the burden.

### Manage your appointments

There's always something on the calendar. Never miss a
dentist appointment, prescription pickup, PT session, or
brunch with friends. Enter your plans, set a reminder,
and put it out of mind until you get a notification from
the service.

### Take the stress out of the holidays

The holidays are coming up -- are you ready? Invite your household
to the service to cover every gift, family meal, greeting card,
and holiday party.

### `POST` example in `curl`: create a new task

```bash
curl -X POST http://{server_url} \
  -H "Content-Type: application/json" \
  -d '{
    "userId": "1",
    "title": "Go to the post office",
    "description": "Mail Star Trek DVDs to Sally",
    "due_date": "2026-11-11T12:00",
    "warning": "60"
  }'
```

[**Get started with the task tutorial >**](/docs/tutorials/add-a-new-task.md)

***
[**Sign Up**](/docs/tutorials/enroll-a-new-user.md) |
[**Tutorials**](/docs/tutorials/tutorials.md) |
[**API Reference**](/docs/index.md#api-reference-docs)
| Copyright &copy; APIDOC310
