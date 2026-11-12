---
# markdownlint-disable
# vale off
layout: default
description: GET and POST examples for the Seafood Restaurant Inventory API using JSON Server.
topic_type: reference
# test:
#   test_apps:
#     - json-server@0.17.4
#   server_url: localhost:3000
#   local_database: /food-db.json
#   testable:
#     - GET example / 200
#     - POST example / 201
# vale on
# markdownlint-enable
---

# Assignment 5.4

<!-- vale Google.Acronyms = off -->

**Author:** `Sharvil Gupta`

The Seafood Restaurant Inventory API manages a list of seafood products available at a restaurant. Each item has an ID, name, price, source location, meat type, quality description, and expiration date. The `/seafood` resource supports retrieving existing items with `GET` and creating new items with `POST`.

## Start the local API server

In the VS Code terminal, navigate to the directory containing `food-db.json` and run:

```bash
npx json-server@0.17.4 --watch food-db.json --port 3000
```

Keep this terminal running while testing the API. The base server URL is `http://localhost:3000`. Requests fail if the server is not running, and the examples assume the uploaded `food-db.json` is the database being served.

## curl examples

These examples use curl to communicate with the local JSON Server API. The base URL `http://localhost:3000` refers to a server running on your own computer; `/seafood` is the resource path. Some templates write this base URL as `{server_url}`. Replace that placeholder with `localhost:3000` when making an actual request.

### `GET` example (curl)

The `GET` request retrieves the seafood item whose ID is `1` from `/seafood/1`. When the item exists, the server returns `200 OK` with a JSON object. A `GET` request does not modify the database.

#### `GET` example request (curl)

```bash
curl -i http://localhost:3000/seafood/1
```

#### `GET` example response (curl)

Expected HTTP status: **200 OK**. Expected response body:

```json
{
  "id": 1,
  "name": "Atlantic Salmon",
  "price": 24.99,
  "importedFrom": "Norway - Atlantic salmon farm",
  "meatType": "Fatty, firm, pink fillet",
  "quality": "Premium, fresh",
  "expirationDate": "2026-11-13"
}
```

### `POST` example (curl)

The `POST` request creates a new seafood entry in the `/seafood` resource. It sends the item attributes in a JSON request body; JSON Server assigns the new entry an ID. The example adds a Branzino item.

#### `POST` example request (curl)

```bash
curl -i -X POST http://localhost:3000/seafood \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Branzino",
    "price": 28.5,
    "importedFrom": "Greece - Mediterranean fish farm",
    "meatType": "Mild, flaky, white fillet",
    "quality": "Premium, fresh",
    "expirationDate": "2026-11-13"
}'
```

#### `POST` example response (curl)

Expected HTTP status: **201 Created**. If the database still contains exactly the original 15 items and IDs 1–15, a typical response body is:

```json
{
  "name": "Branzino",
  "price": 28.5,
  "importedFrom": "Greece - Mediterranean fish farm",
  "meatType": "Mild, flaky, white fillet",
  "quality": "Premium, fresh",
  "expirationDate": "2026-11-13",
  "id": 16
}
```

The ID shown is illustrative, not a response captured from a running server. The actual assigned ID may differ, especially after other `POST` requests.

## Postman examples

These examples use Postman to send a `GET` request and a `POST` request to the same local Seafood Restaurant Inventory API. Enter the URL in Postman's request URL field, choose the specified HTTP method, and click **Send**. The expected status codes are `200 OK` for retrieval and `201 Created` for creation.

### `GET` example (Postman)

The `GET` request looks up the existing Atlantic Salmon entry by its ID (`1`). It returns item information without changing the source database.

#### `GET` example request (Postman)

**Method:** `GET`  
**URL:** `http://localhost:3000/seafood/1`  
**Body:** None  
**Action:** Click **Send**.

#### `GET` example response (Postman)

Expected status: **200 OK**. Under **Body → Pretty → JSON**, the expected response is:

```json
{
  "id": 1,
  "name": "Atlantic Salmon",
  "price": 24.99,
  "importedFrom": "Norway - Atlantic salmon farm",
  "meatType": "Fatty, firm, pink fillet",
  "quality": "Premium, fresh",
  "expirationDate": "2026-11-13"
}
```

### `POST` example (Postman)

The `POST` request creates a new Branzino seafood entry. Select `POST`, use the `/seafood` collection URL, configure the JSON content type, and submit the request body.

#### `POST` example request (Postman)

**Method:** `POST`  
**URL:** `http://localhost:3000/seafood`  
**Action:** Click **Send** after adding the following header and body.

##### `POST` request headers (Postman)

Under the **Headers** tab, add this request header:

| Key | Value |
| --- | --- |
| `Content-Type` | `application/json` |

This is a *request* header. Server-generated *response* headers such as `Date`, `ETag`, and `Content-Length` are not known in advance and depend on the actual response.

##### `POST` request data (Postman)

Select **Body → raw → JSON** and paste:

```json
{
  "name": "Branzino",
  "price": 28.5,
  "importedFrom": "Greece - Mediterranean fish farm",
  "meatType": "Mild, flaky, white fillet",
  "quality": "Premium, fresh",
  "expirationDate": "2026-11-13"
}
```

#### `POST` example response (Postman)

Expected status: **201 Created**. If no new items were added before this request, an illustrative response body is:

```json
{
  "name": "Branzino",
  "price": 28.5,
  "importedFrom": "Greece - Mediterranean fish farm",
  "meatType": "Mild, flaky, white fillet",
  "quality": "Premium, fresh",
  "expirationDate": "2026-11-13",
  "id": 16
}
```

**Important:** Each `POST` creates another record. If you run the curl `POST` example first and then the Postman `POST` example, the second response typically receives a different ID. The examples show expected behavior based on the supplied database; they were not captured from an actual running VS Code server.

## Verify the new item

After a successful `POST`, retrieve the entire seafood collection to see the new record:

```bash
curl http://localhost:3000/seafood
```

Or retrieve the new item using the ID returned in the `POST` response:

```bash
curl http://localhost:3000/seafood/16
```

Replace `16` with the actual returned ID if necessary. JSON Server generally saves created records back to `food-db.json`.
gi