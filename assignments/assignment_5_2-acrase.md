# Assignment 5.2 - Open API Specification document

## Manually created OAS document

```yaml
openapi: 3.0.3
info:
  title: The dog database
  version: 0.0.1
  contact:
    name: Allison Crase
servers:
  - url: http://localhost:3000
paths:
  /dogs:
    get:
     summary: Get all dogs
     operationId: getAllDogs
     responses:
      '200':
       description: "A list of dogs"
       content:
         application/json:
           schema:
             type: object
             properties:
               dogs:
                 type: array
                 items:
                   type: object
                   properties:
                     id:
                       type: string
                     breed:
                       type: string
                     color:
                       type: string
                     weight:
                       type: number

```