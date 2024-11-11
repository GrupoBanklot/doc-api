# Lottery API Documentation

## Table of Contents
- [Lottery API Documentation](#lottery-api-documentation)
  - [Table of Contents](#table-of-contents)
  - [- **Endpoint**s](#--endpoints)
  - [Verbs](#verbs)
  - [Status Codes](#status-codes)
  - [Authentication](#authentication)
    - [Login](#login)
    - [Logout](#logout)
  - [Queries](#queries)
    - [Ticket View](#ticket-view)
    - [View Printed Ticket](#view-printed-ticket)
    - [View Last Ticket](#view-last-ticket)
    - [Cancel Ticket View](#cancel-ticket-view)
    - [Winner Ticket View](#winner-ticket-view)
    - [Sold Tickets](#sold-tickets)
    - [Get Data](#get-data)
  - [Actions](#actions)
    - [Pay Tickets](#pay-tickets)
    - [Copy Tickets](#copy-tickets)
    - [Cancel a Ticket](#cancel-a-ticket)
    - [Revert a Ticket](#revert-a-ticket)
    - [Create a Ticket](#create-a-ticket)
  - [Reports](#reports)
    - [Report Per Period](#report-per-period)
    - [Results Report](#results-report)
  - [Kiosk](#kiosk)
    - [Valid Plays](#valid-plays)
    - [Hour](#hour)
    - [Draw](#draw)
    - [Products](#products)

---

## - **Endpoint**s
API calls to the Grupo Banklot portal use the following base URL:

https://prueba.gatobets.com/

markdown

API calls listed below will provide the URL that must be appended to this **endpoint** when making requests.

## Verbs
The following HTTP verbs are used. Please refer to each API individually for the appropriate syntax for resource creation or update as they can use one of PUT, `POST`, or PATCH.

- `GET` - retrieve a resource
- `PUT` - update a resource
- `PATCH` - update a resource
- ``POST`` - create a resource
- `DELETE` - delete a resource

## Status Codes
The status codes returned by the API include the following:

- `200 OK` - the request was successful
- `201 Created` - the resource was created
- `204 No Content` - the request was successful, but there is no data to return
- `301 Moved Permanently` - the resource can be accessed through another URL
- `400 Bad Request` - there is an issue with the request you submitted
- `403 Forbidden` - authentication failure, or deprecated API version
- `404 Not Found` - resource not found
- `500 Internal Server Error` - there's an error on our side, email us!

## Authentication

### Login

To login with credentials, call:

- **Endpoint**: `/auth/login`
- **Method**: `POST`
- **Headers**:

 -`Content-Type: application/json`

```json
{
  "email": "username@banklot.net",
  "password": "******"
}
```

Response: Retrieves a token and sets it in the environment variable for future requests.

### Logout

To log out of the existing session, call:

- **Endpoint**: `/auth/logout`
- **Method**: `GET`
- **Headers**: x-auth-token must be set.

## Queries

### Ticket View

- **Endpoint**: `/user/ticket
- **Method**: `POST`
- **Headers**:

 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket_number": 32426439,
  "date": "2024-10-22"
}
```

Response:

```json
{
  "status": 201,
  "response": {
    "ticket_number": 32426439,
    "pin_number": 76479163,
    "num_wagers": 6,
    "entity_id": 213,
    "parent_id": 212,
    "entity_name": "test-1",
    "parent_name": "test",
    "created_at": 1729587036,
    "wagers": [
      {
        "amount": 3,
        "current_event_id": 23336,
        "event_id": 23173,
        "event_name": "ASTRO ZAMORANO",
        "game_id": 3,
        "list_id": 3,
        "p_event_time": "12:00 pm",
        "status": "sold",
        "wager": "444-ARI"
      }
    ],
    "amount": 18
  }
}
  ```

### View Printed Ticket

- **Endpoint**: `/user/ticket/image/f3f30cdb-2165-487b-bfd0-c990b7ab62c1`
- **Method**:`GET`
- **Headers**:
 -`Content-Type: application/json`

### View Last Ticket

- **Endpoint**: `/user/ticket/last`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body: No body is required.
Response:

```json
{
  "status": 202,
  "response": {
    "ticket_number": 10063292,
    "pin_number": 38037945,
    "num_wagers": 3,
    "entity_id": 213,
    "parent_id": 212,
    "entity_name": "test-1",
    "parent_name": "test",
    "created_at": 1729664000,
    "wagers": [
      {
        "amount": 22,
        "current_event_id": 23301,
        "event_id": 23301,
        "event_name": "JUNGLA MILLONARIA",
        "game_id": 5,
        "p_event_time": "09:00 am",
        "status": "sold",
        "wager": "0"
      }
    ],
    "amount": 66
  }
}
```

### Cancel Ticket View

- **Endpoint**: `/user/ticket/`
- **Method**: `POST`
- **Headers**:

 -`Content-Type: application/json`

Request Body:

```json
{
  "filter": {
    "between_created_at": [
      "2024-06-05T04:00:00.000Z",
      "2024-10-23T03:59:59.999Z"
    ],
    "status": "canceled"
  },
  "sort": {
    "created_at": 1
  }
}
```

### Winner Ticket View

- **Endpoint**: `/user/ticket/`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "filter": {
    "between_created_at": [
      "2024-10-01T04:00:00.000Z",
      "2024-10-23T03:59:59.999Z"
    ],
    "status": "winner"
  },
  "sort": {
    "created_at": 1
  }
}
```

### Sold Tickets

- **Endpoint**: `/user/ticket/`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "filter": {
    "between_created_at": [
      "2024-08-28T04:00:00.000Z",
      "2024-08-29T03:59:59.999Z"
    ],
    "transaction_type": "wager"
  },
  "order_by": [
    {
      "name": "created_at",
      "value": "desc"
    }
  ]
}
```

### Get Data

- **Endpoint**: `/gaming/get-data`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`
Response:

```json
{
  "status": 200,
  "response": {
    "entity_id": 213,
    "name": "test-1",
    "status": "active",
    "games": [
      "animalitos77",
      "animalitos",
      "tripleta",
      "lottery"
    ]
  }
}
```

## Actions

### Pay Tickets

- **Endpoint**: `/user/ticket/pay`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket_number": 10653459,
  "pin_number": 84038675,
  "date": "2024-09-16"
}
```

Response:

```json
{
  "status": 200,
  "error": "not a winner"
}
```

### Copy Tickets

- **Endpoint**: `/user/ticket/copy`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket_number": 71998218,
  "date": "2024-09-17"
}
```

Response:

```json
{
  "status": 201,
  "response": {
    "ticket_uuid": "362a5a41-2ac4-4c8f-a8f7-a907f86e4426",
    "ticket_number": 71998218,
    "num_wagers": 1
  }
}
  ```

### Cancel a Ticket

- **Endpoint**: `/user/ticket/cancel`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket_number": 18712010
}
```

Response:

```json
{
  "status": 400,
  "error": "no rows in result set"
}
  ```

### Revert a Ticket

- **Endpoint**: `/user/ticket/revert`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket_number": 71998218
}
```

Response:

```json
{
  "status": 401,
  "error": "ticket already rejected by user"
}
```

### Create a Ticket

- **Endpoint**: `/user/ticket/create`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "ticket": {
    "wagers": [
      {
        "amount": 2000,
        "event_id": 18859,
        "game_id": 1,
        "wager": "341"
      }
    ]
  }
}
```

Response:

```json
{
  "status": 409,
  "error": "events are not open. closed events: [18859]"
}
```

## Reports

### Report Per Period

- **Endpoint**: `/gaming/reports`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "between_timestamp": [
    "2024-06-27T04:00:00.000Z",
    "2024-06-28T03:59:59.999Z"
  ],
  "group": "user",
  "category": "lottery"
}
```

Response:

```json
{
  "status": 200,
  "total": {
    "agency": 0,
    "balance": 0,
    "parent_balance": 0,
    "prize": 0,
    "sale": 0
  }
}
```

### Results Report

- **Endpoint**: `/gaming/result/0`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "filter": {
    "between_created_at": [
      "2024-08-18T04:00:00.000Z",
      "2024-09-18T03:59:59.999Z"
    ]
  },
  "order_by": [
    {
      "name": "event_timestamp",
      "value": "desc"
    }
  ]
}
```

## Kiosk

### Valid Plays

- **Endpoint**: `/gaming/inventory/template`
- **Method**: `POST`
- **Headers**:
    -`Content-Type: application/json`

Response:

```json
{
    "status": 200,
    "response": [
        {
            "game_id": 1,
            "wager": "001",
            "code": "001"
        },
        {
            "game_id": 1,
            "wager": "002",
            "code": "002"
        },
    ]
}
```

### Hour

- **Endpoint**: `/gaming/time`
- **Method**: `GET`

Request Body:

```json

{
  "filter": {
    "between_created_at": [
      "2024-04-21",
      "2024-04-21"
    ]
  },
  "sort": {
    "event_timestamp": "desc"
  }
}
```
  
### Draw

- **Endpoint**: `/gaming/events/search/kiosk`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`

Request Body:

```json
{
  "filter": {
    "between_created_at": [
      "2024-06-05T04:00:00.000Z",
      "2024-06-06T03:59:59.999Z"
    ],
    "game_category": "lottery",
    "status": "open"
  },
  "sort": {
    "game_category": "desc",
    "event_timestamp": "desc",
    "display_order": "0"
  }
}
```

Response:

```json
{
    "status": 201,
    "total": 0
}
```

### Products

- **Endpoint**: `/gaming/products/search`
- **Method**: `POST`
- **Headers**:
 -`Content-Type: application/json`