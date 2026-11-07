---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: Tutorials
nav_order: 3
# tags used by AI files
description: Update a `user` resource in the service
topic_type: tutorial
tags:
    - api
categories: 
    - tutorial
ai_relevance: high
importance: 6
prerequisites: 
    - /before-you-start-a-tutorial
    - /api/user
related_pages: []
examples: []
api_endpoints: 
    - POST /users
version: "v1.0"
last_updated: "2026-11-07"
# vale  on
# markdownlint-enable
---
# Tutorial - edit a user

<!-- vale Google.Acronyms = off -->
The To-Do Service is a REST API that can help you
and your friends manage tasks within minutes.

A useful function of the service is to **edit**
information for
an [existing user](../api/user.md).

**In this tutorial, you'll learn**:

- How to retrieve a user's ID number

- How to edit information for that user

The `PATCH` method utilized here allows you to make
**partial** changes to an existing resource without
overwriting other data.

This can be useful if, for example, a friend changes schools
and gets a new email address. Or maybe your cousin
got married and took their partner's last name. With this
tutorial, you can follow the steps below to quickly update
user contact info in the To-Do Service.

## Step 1: find the user's ID number

Before you attempt the request to change the user's info,
you need to have their ID number if you don't already.

1. Request a list of users
with the following `curl` command, substituting
your actual server URL for
`{{server_url}}`:

    ```bash
    curl {{server_url}}/users
    ```

2. Review the response and locate the user's ID number. For
example, say your friend is Buffy Summers, and your
request returns the following response. Buffy's ID number is
**2**.

    ```bash
    [
        {
        "lastName": "Rupert",
        "firstName": "Giles",
        "email": "the.watcher@sunnydale.edu",
        "id": "1"
      },
      {
        "lastName": "Summers",
        "firstName": "Buffy",
        "email": "vmprslyr@sunnydale.edu",
        "id": "2"
      }
    ]
    ```

## Step 2: edit the email address

Now that you have the ID number, send a `PATCH` request
to update the email contact.

1. Enter the following `curl`
command, substituting `{{server_url}}`
with your server URL, `{{id}}` with the user ID number, and
`{{email_address}}` with the actual email address.

    ``` bash
    curl -X PATCH http://{{server_url}}/users/{{id}} \
     -H "Content-Type: application/json" \
     -d '{"email": "{{email_address}}"}'
    ```

2. Review the response and confirm that the email address
updated properly. An updated result using the previous
example would look like the following example. Note that
the email address updated from `vmprslyr@sunnydale.edu`
to `bsummers@ucs.edu`, while the rest of the values
didn't change.

    ```bash
    {
      "lastName": "Summers",
      "firstName": "Buffy",
      "email": "bsummers@ucs.edu",
      "id": "2"
    }
    ```

## Wrap-up and next steps

Awesome &mdash; you edited an existing user's email
information by first getting their ID number and then
sending a `PATCH` request to update the value.

If you got stuck, refer to the **Troubleshooting** section below.

### Related topics

- [**Add your first user >**](../tutorials/enroll-a-new-user.md)

- [**Add your first task >**](../tutorials/add-a-new-task.md)

## Troubleshooting

- Ensure you have the correct ID number when sending the
`PATCH` request, or you can update the wrong user's email.
- If the response includes a new, unexpected value, you
likely mistyped `email` and added a new property.
- **Couldn't resolve host error**: make sure you input your
server URL into the command correctly.
- **Returned a response of `{}`**: make sure you input the
correct ID number, as you may have entered one that doesn't
exist.

***
[**Sign Up**](../tutorials/enroll-a-new-user.md) |
[**Tutorials**](../tutorials.md) |
[**API Reference**](../../docs/index.md#api-reference-docs)
| Copyright &copy; APIDOC310
