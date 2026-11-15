---
# markdownlint-disable
# vale off
# tags used by just-the-docs theme
layout: default
parent: Tutorials
nav_order: 4
# tags used by AI files
description: Get a `user` resource by its `id`
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
    - GET /users
version: "v1.0"
last_updated: "2026-11-07"
# vale  on
# markdownlint-enable
---

# Tutorial:  Get user by ID

In this tutorial, you'll learn how to perform the GET / users/{userId} operation.

## Before you start

Follow the steps in the doc [Before you start a tutorial](../before-you-start-a-tutorial.md).

## Get user by ID

To retrieve a user by ID, use the `GET` method.

1. Make sure your local service is running. If not, use this command.

    ```shell
    cd <your-github-workspace>/to-do-service/api
    json-server -w to-do-db-source.json
    ```

2. Open the Postman app on your desktop.
3. In the Postman app, create a new request with these values:
    * **METHOD**:`POST`
    * **URL**: `{{base_url}}/users/{userID}`
    * **Headers**:
        * `Content-Type: application/json`
    * **Request body**:
        None

4. In the Postman app, choose **Send** to make the request.
5. The response body returns a user resource.
For example, using the {userID} 2 returns this user data.

```json
{
    
    "lastName": "Jones",
    "firstName": "Jill",
    "email": "j.jones@example.com",
    "id": 2
    
}
```
