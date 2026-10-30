---
# markdownlint-disable
# vale off

layout: default
description: API endpoint for vacations and transportation
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

# Vacations and transportation API

<!-- vale Google.Acronyms = off -->

**Author:** `Ainsley Elder`

This endpoint allows you to create and edit lists of vacation places
and transport.

## curl examples

These examples show how to retrieve and create vacation and
transport options via a local server.

### `GET` example (curl)

This example retrieves a specific vacation by ID number. The response
includes the country, city, housing type, locale, and ID
number of the vacation.

#### `GET` example request (curl)

```bash
curl http://{server_url}/vacations/1
```

#### `GET` example response (curl)

```json
{
  "country": "Mexico",
  "city": "Cancun",
  "housing": "Resort",
  "locale": "beach",
  "id": 1
}
```

### `POST` example (curl)

This example creates a new transport entry that
includes industry, vehicle, class, price, and assigns
an ID number.

#### `POST` example request (curl)

```bash
$ curl -X POST http://localhost:3000/transportation \
  -H "Content-Type: application/json" \
  -d '{
    "industry": "sea",
    "vehicle": "cruise ship",
    "class": "fancy",
    "price": "expensive"
  }'
```

#### `POST` example response (curl)

```json
{
  "industry": "sea",
  "vehicle": "cruise ship",
  "class": "fancy",
  "price": "expensive",
  "id": 2
}
```
