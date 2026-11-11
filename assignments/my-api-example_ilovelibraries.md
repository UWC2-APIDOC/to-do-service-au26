---
# markdownlint-disable
# vale off

layout: default
description: This API is a sample product database for a company selling apparel and accessories.
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

# {INSERT page title}

<!-- vale Google.Acronyms = off -->

**Author:** `Rebecca Simms`

This API is a sample product database for a company selling apparel and accessories.

## curl examples

This section demonstrates example curl GET and POST examples
using the product database API. {server_url} is a placeholder URL.

### `GET` example (curl)

This GET request example pulls the JSON data for the apparel product.

#### `GET` example request (curl)

```bash
curl http://{server_url}/apparel
```

#### `GET` example response (curl)

```json
[
  {
    "Product Type": "T-shirt",
    "Sleeve Length": "short",
    "Fabric": "cotton",
    "Color": "white",
    "id": 1
  }
]

```

### `POST` example (curl)

{REPLACE WITH a description of the `POST` request and what it creates.}

#### `POST` example request (curl)

```bash
curl -X POST http://{server_url/apparel \
  -H "Content-Type: application/json" \
  -d '{
    "Product Type": "Sweatshirt",
    "Sleeve Length": "long",
    "Fabric": "fleece",
    "Color": "blue"
  }'

```

#### `POST` example response (curl)

```json
{
  "Product Type": "Sweatshirt",
  "Sleeve Length": "long",
  "Fabric": "fleece",
  "Color": "blue",
  "id": 3
}
```
