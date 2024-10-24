## Table of Contents

| Section                  |                                      |
|--------------------------|--------------------------------------|
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


Welcome to the ****Grupo Banklot**** developer portal. Here you will find a reference for how to integrate **Grupo Banklot** into your existing applications and workflows using our [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) [HTTPS](https://en.wikipedia.org/wiki/HTTPS)-based API. Our API uses standard [HTTP verbs](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods) to specify the intent of the operation, and HTTP[ status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) to indicate the response to those operations. Security tokens are issued on login which are included as [HTTP headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields).

Use the language selector at the top to show examples in your language of choice, and use the version selector within the code sample for each API to see a sample request/response for that particular version.

# EndPoints

API calls to the ****Grupo Banklot**** portal use the following base URL:

[https://staging.loterias24.com/](https://staging.loterias24.com/)

API calls listed below will provide the URL that must be appended to this endpoint when making requests.

#
# Verbs

The following HTTP verbs are used. A description of how each is used is shown. Please refer to each API individually for the appropriate syntax for resource creation or update as they can use one of PUT, POST, or PATCH.

- GET - retrieve a resource

- PUT - update a resource

- PATCH - update a resource

- POST - create a resource

- DELETE - delete a resource

# Status Codes

The status codes returned by the API include the following:

- 200 - OK - the request was successful

- 201 - Created - the resource was created

- 204 - No Content - the request was successful, but there is no data to return

- 301 - Moved Permanently - the resource can be accessed through another URL

- 400 - Bad Request - there is an issue with the request you submitted

- 403 - Forbidden - authentication failure, or deprecated API version

- 404 - Not Found - resource not found

- 500 - Internal Server Error - there's an error on our side, email us!


# Authentication

## **Login**

Authentication involves the use of a single API. However, multiple authentication and administrative APIs should be used in succession to retrieve the appropriate metadata to use to query the API.

1. To login with credentials, call POST /auth/login. The request body should include the following key-value pairs.

```{python}
**Endpoint**: **/auth/login** 
**Method:** **POST** 
**Headers:**

- **Content-Type: ****application/json**** **

- **Request Body:**
```

```{python} 
{
    "email": "username@banklot.net", 
    "password": "******"
}
```

- Response:

- Retrieves a token and sets it in the environment variable for future requests.

- Event Script:

- Parses the response body and sets the token in the environment

**IMPORTANT ** *Upon a successful response, extract the *`x_auth_token`* value from the JSON response. This value is the security token which must be included in subsequent API calls using the *`x-auth-token header`*.*

# **Logout**

To log out of the existing session, call `GET ``/auth/logout` with the** **`x-auth-token` set.

## Queries

## **Ticket View**
```{bash}
**Endpoint**: **/user/ticket** 
**Method:** **POST** 
**Headers:**
```
- **Content-Type: ****application/json**** **

- **Request Body:**

**Request:**

```{bash}
{
    "ticket_number": 32426439,
    "date": "2024-10-22"
}

```

**Response:**

```
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
            },
            {
                "amount": 3,
                "current_event_id": 23336,
                "event_id": 23173,
                "event_name": "ASTRO ZAMORANO",
                "game_id": 3,
                "list_id": 3,
                "p_event_time": "12:00 pm",
                "status": "sold",
                "wager": "444-CAN"
            },
            {
                "amount": 3,
                "current_event_id": 23336,
                "event_id": 23173,
                "event_name": "ASTRO ZAMORANO",
                "game_id": 3,
                "list_id": 3,
                "p_event_time": "12:00 pm",
                "status": "sold",
                "wager": "444-ACU"
            },
            {
                "amount": 3,
                "current_event_id": 23310,
                "event_id": 23147,
                "event_name": "ZODÍACO DEL ZULIA",
                "game_id": 3,
                "list_id": 3,
                "p_event_time": "12:45 pm",
                "status": "sold",
                "wager": "444-ARI"
            },
            {
                "amount": 3,
                "current_event_id": 23310,
                "event_id": 23147,
                "event_name": "ZODÍACO DEL ZULIA",
                "game_id": 3,
                "list_id": 3,
                "p_event_time": "12:45 pm",
                "status": "sold",
                "wager": "444-CAN"
            },
            {
                "amount": 3,
                "current_event_id": 23310,
                "event_id": 23147,
                "event_name": "ZODÍACO DEL ZULIA",
                "game_id": 3,
                "list_id": 3,
                "p_event_time": "12:45 pm",
                "status": "sold",
                "wager": "444-ACU"
            }
        ],
        "amount": 18
    }
}
```
## ## **View Printed Ticket**

**Endpoint**:** /user/ticket/image/f3f30cdb-2165-487b-bfd0-c990b7ab62c1 \
****Method: ****GET \
****Headers:**

- **Content-Type: ****application/json**** **

**Request: **Ticket must have the uuid format** **as part of the URL not the body.

**Response:**

```

```
## ## 
## View Last Ticket

**Endpoint**:** /user/ticket/last \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **No body is required.

**Response**:

```
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
                "list_id": null,
                "p_event_time": "09:00 am",
                "status": "sold",
                "wager": "0"
            },
            {
                "amount": 22,
                "current_event_id": 23301,
                "event_id": 23301,
                "event_name": "JUNGLA MILLONARIA",
                "game_id": 5,
                "list_id": null,
                "p_event_time": "09:00 am",
                "status": "sold",
                "wager": "1"
            },
            {
                "amount": 22,
                "current_event_id": 23301,
                "event_id": 23301,
                "event_name": "JUNGLA MILLONARIA",
                "game_id": 5,
                "list_id": null,
                "p_event_time": "09:00 am",
                "status": "sold",
                "wager": "2"
            }
        ],
        "amount": 66
    }
}
```
## Cancel Ticket View

**Endpoint**:** /user/ticket/ \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the date time range with the status.

**Request: **Must specified the date time range

```
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

**Response**:

```
{
    "status": 200,
    "response": [
        {
            "id": "639a1521-49b9-4876-a36c-36c621593930",
            "ticket_number": 13239361,
            "created_at": 1721660369,
            "user_id": 864,
            "email": "taquilla@banklot.net",
            "status": "canceled",
            "total": 6,
            "prize": 0,
            "entity_id": 213,
            "parent_id": 212,
            "entity_name": "test-1",
            "parent_name": "test"
        },
       ],
   }
```

## Winner Ticket View

**Endpoint**:** /user/ticket/ \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the date time range with the status

**Request:**

```
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

**Response:**

```
    "status": 200,
    "response": [
        {
            "id": "af681029-87a2-4834-b7f9-56d88ee3a74e",
            "ticket_number": 23315522,
            "created_at": 1728066656,
            "user_id": 864,
            "email": "taquilla@banklot.net",
            "status": "winner",
            "total": 33,
            "prize": 330,
            "entity_id": 213,
            "parent_id": 212,
            "entity_name": "test-1",
            "parent_name": "test"
        },

```

## Sold Tickets

**Endpoint**:** /user/ticket/ \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the date time range with the transaction_type

**Request:**

```
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
**Response:**

```
{
    "status": 200,
    "response": [
        {
            "id": "16baefc2-5c3e-4f17-a26c-c19808e22655",
            "ticket_number": 30213646,
            "created_at": 1724896556,
            "user_id": 864,
            "email": "taquilla@banklot.net",
            "status": "sold",
            "total": 10,
            "prize": 0,
            "entity_id": 213,
            "parent_id": 212,
            "entity_name": "test-1",
            "parent_name": "test"
        },
],
}
```

## Get Data

**Endpoint**:** /gaming/get-data \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body:**

**Response:**

```
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
        ],
        "entity_data": {
            "address1": "",
            "address2": "",
            "city": "",
            "municipality": 1,
            "rif": "1234",
            "seconds_to_cancel": 180,
            "state": 3,
            "ticket_expiration_days": 3,
            "ticket_footer": "123",
            "ticket_header": "123",
            "time_zone": "America/Caracas"
        },
        "game_data": [
            {
                "amount_multiple": 1,
                "commission": 10,
                "game_id": 1,
                "max_bet": 99,
                "max_permutations": 6,
                "max_sequence_size": 10,
                "max_sequences": 2,
                "min_bet": 1,
                "product_id": 1,
                "ticket_max_wagers": 100
            },
            {
                "amount_multiple": 1,
                "commission": 10,
                "game_id": 1,
                "max_bet": 99,
                "max_permutations": 6,
                "max_sequence_size": 10,
                "max_sequences": 2,
                "min_bet": 1,
                "product_id": 2,
                "ticket_max_wagers": 100
            },
            {
                "amount_multiple": 1,
                "commission": 10,
                "game_id": 1,
                "max_bet": 99,
                "max_permutations": 6,
                "max_sequence_size": 10,
                "max_sequences": 2,
                "min_bet": 1,
                "product_id": 3,
                "ticket_max_wagers": 100
            },

```

# Actions

## Pay Tickets

**Endpoint**:** /user/ticket/pay \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the ticket number, pin_number and date.

**Request:**

```
{
  "ticket_number": 10653459,
  "pin_number": 84038675,
  "date": "2024-09-16"  
}
```
**Response:**

```
{
    "status": 200,
    "error": "not a winner"
}
```

## Copy Tickets

**Endpoint**:** /user/ticket/copy \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the ticket number and date. 

**Request:**

```
{
  "ticket_number": 71998218,
  "date": "2024-09-17"  
}
```
**Response:**

```
{
    "status": 201,
    "response": {
        "ticket_uuid": "362a5a41-2ac4-4c8f-a8f7-a907f86e4426",
        "ticket_number": 71998218,
        "num_wagers": 1,
        "wagers": [
            {
                "amount": 5,
                "event_id": 23335,
                "game_id": 1,
                "old_event_id": 18748,
                "wager": "001"
```
## Cancel a Ticket

**Endpoint**:** /user/ticket/cancel \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the ticket number

**Request:**

```
{
  "ticket_number": 18712010
}
```
**Response:**

```
{
    "status": 400,
    "error": "no rows in result set"
}
```

## Revert a Ticket

**Endpoint**:** /user/ticket/revert \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the ticket number

**Request:**

```
{
  "ticket_number": 71998218
}
```
**Response:**

```
{
    "status": 401,
    "error": "ticket already rejected by user"
}
```
## ## **Create a Ticket**

**Endpoint**:** /user/ticket/create \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the amount, event_id, game_id, and the wager.

**Request:**

```
{
    "ticket": {
        "wagers":
            [
                {
                    "amount": 2000,
                    "event_id": 18859,
                    "game_id": 1,
                    "wager": "341"
                },
                {
                    "amount": 2000,
                    "event_id": 18859,
                    "game_id": 1,
                    "wager": "000"
                }
            ]

    }}
```
**Response:**

```
{
    "status": 409,
    "error": "events are not open. closed events: [18859]"
}
```

# Reports

## Report Per Period

**Endpoint**:** /gaming/reports \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the date time range, group and category.

**Request:**

```
{
  "between_timestamp": [
    "2024-06-27T04:00:00.000Z",
    "2024-06-28T03:59:59.999Z"
  ],
  "group": "user",
  "category": "lottery" 
}
```

**Response:**

```
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

## Results Report

**Endpoint**:** /gaming/result/0 \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain the date time range.

**Request:**

```
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

**Response:**

```
{
    "status": 200,
    "response": [
        {
            "id": 18697,
            "game_product_id": 6,
            "name": "JUNGLA MILLONARIA",
            "event_time": "16:00",
            "event_time_utc": "20:00",
            "closing_timestamp": {
                "seconds": 1729713300
            },
            "game_category": "animalitos",
            "status": "result",
            "event_timestamp": {
                "seconds": 1726603200
            },
            "display_order": 20,
            "main_result": "5",
            "event_status": "closed",
            "result_created_at": {
                "seconds": 1726545660,
                "nanos": 192719000
            }
        },
        {
            "id": 18732,
            "game_product_id": 1,
            "name": "TRIPLE ZAMORANO",
            "event_time": "16:00",
            "event_time_utc": "20:00",
            "closing_timestamp": {
                "seconds": 1729713300
            },
            "game_category": "lottery",
            "status": "result",
            "event_timestamp": {
                "seconds": 1726603200
            },
            "display_order": 19,
            "list": "C",
            "list_id": 3,
            "main_result": "000-ACU",
            "event_status": "closed",
            "zodiac": true,
            "result_created_at": {
                "seconds": 1726545660,
                "nanos": 192719000
            }
        },
        {
            "id": 18731,
            "game_product_id": 1,
            "name": "TRIPLE ZAMORANO",
            "event_time": "16:00",
            "event_time_utc": "20:00",
            "closing_timestamp": {
                "seconds": 1729713300
            },
            "game_category": "lottery",
            "status": "result",
            "event_timestamp": {
                "seconds": 1726603200
            },
            "display_order": 19,
            "list": "A",
            "list_id": 1,
            "main_result": "000",
            "event_status": "closed",
            "result_created_at": {
                "seconds": 1726545660,
                "nanos": 192719000
            }
        },
        {
            "id": 18694,
            "game_product_id": 6,
            "name": "JUNGLA MILLONARIA",
            "event_time": "15:00",
            "event_time_utc": "19:00",
            "closing_timestamp": {
                "seconds": 1729709700
            },
            "game_category": "animalitos",
            "status": "result",
            "event_timestamp": {
                "seconds": 1726599600
            },
            "display_order": 17,
            "main_result": "2",
            "event_status": "closed",
            "result_created_at": {
                "seconds": 1726545660,
                "nanos": 192719000
            }
        },

```
# Kiosk

## Valid Plays

**Endpoint**:**/gaming/inventory/template \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **No body is required. 

**Response:**

```
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
```

## Hour

**Endpoint**:** /gaming/time \
****Method: ****GET \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body:**

**Request:**

```
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

**Response:**

```

```
## ## **Draw**

**Endpoint**:**/gaming/events/search/kiosk \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **Must contain date time range, game category and status.

**Request:**

```
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

**Response:**

```
{
    "status": 201,
    "total": 0
}
```

## Products

**Endpoint****:/gaming/products/search \
****Method: ****POST \
****Headers:**

- **Content-Type: ****application/json**** **

- **Request Body: **No body parameters are required.

**Response:**

```
{
    "status": 201,
    "response": [
        {
            "id": 17,
            "name": "TRIPLE DORADO",
            "lottery": "LOTERIA DE GUAYANA",
            "lottery_id": 22,
            "status": "active",
            "quota": 1000000,
            "game_category": "lottery",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23286,
                    "event_time": "14:00:00",
                    "next_event_date": "2024-10-24",
                    "next_event_time": "12:00:00"
                }
            ]
        },
        {
            "id": 30,
            "name": "LOTTO REY",
            "lottery": "LOTERIA DE MARGARITA",
            "lottery_id": 24,
            "status": "active",
            "quota": 1000000,
            "game_category": "animalitos",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23431,
                    "event_time": "13:30:00",
                    "next_event_date": "2024-10-24",
                    "next_event_time": "11:30:00"
                }
            ]
        },
        {
            "id": 18,
            "name": "GUACHARO ACTIVO",
            "lottery": "LOTERÍA DE ORIENTE",
            "lottery_id": 23,
            "status": "active",
            "quota": 1000000,
            "game_category": "animalitos77",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23346,
                    "event_time": "14:00:00",
                    "next_event_date": "2024-10-24",
                    "next_event_time": "12:00:00"
                }
            ]
        },
        {
            "id": 27,
            "name": "TRIPLE CHANCE",
            "lottery": "LOTERÍA DE ORIENTE",
            "lottery_id": 23,
            "status": "active",
            "quota": 1000000,
            "game_category": "lottery",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23366,
                    "event_time": "16:30:00",
                    "next_event_date": "2024-10-23",
                    "next_event_time": null
                }
            ]
        },
        {
            "id": 2,
            "name": "TRIPLE ZULIA",
            "lottery": "LOTERÍA DEL ZÚLIA",
            "lottery_id": 1,
            "status": "active",
            "quota": 1000000,
            "game_category": "lottery",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23311,
                    "event_time": "16:45:00",
                    "next_event_date": "2024-10-23",
                    "next_event_time": null
                }
            ]
        },
        {
            "id": 1,
            "name": "TRIPLE ZAMORANO",
            "lottery": "LOTERÍA DEL ZÚLIA",
            "lottery_id": 1,
            "status": "active",
            "quota": 100,
            "game_category": "lottery",
            "lottery_status": "active",
            "data": [
                {
                    "event_date": "2024-10-23",
                    "event_id": 23316,
                    "event_time": "16:00:00",
                    "next_event_date": "2024-10-23",
                    "next_event_time": null
                }
            ]
        },

```