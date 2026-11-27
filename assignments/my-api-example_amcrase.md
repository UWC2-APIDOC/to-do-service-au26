---
# markdownlint-disable
# vale off

layout: default
description: Types of Dogs
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

# Types of Dogs

  <!-- vale off -->
  Author: Aly Crase
  <!-- vale on -->

## curl examples

{REPLACE WITH an overview of this section. Be sure to explain what {server_url} means if you use it.}

### `GET` example (curl)

{REPLACE WITH a description of the `GET` request and what it returns.}

#### `GET` example request (curl)

```bash
curl http://localhost:3000/dogs
```

#### `GET` example response (curl)

```json
{
"breed": "Beagle",
"color": "tricolor",
"weight": "24"
}
```

### `POST` example (curl)

Will show you the breed of a dog.

#### `POST` example request (curl)

```bash
curl -X POST http://localhost:3000/dogs \
  -H "Content-Type: application/json" \
  -d '{
    "breed": "Beagle",
    "color": "tricolor",
    "weight": "24"
  }'
```

#### `POST` example response (curl)

```json
{
"breed": "Beagle",
"color": "tricolor",
"weight": "24"
}
```
