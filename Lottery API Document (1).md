

[**EndPoints	3**](#endpoints)

[**Verbs	4**](#verbs)

[**Status Codes	4**](#status-codes)

[**Authentication	5**](#authentication)

[Login	5](#login)

[Logout	5](#logout)

[**Queries	7**](#queries)

[Ticket View	7](#ticket-view)

[View Printed Ticket	10](#view-printed-ticket)

[View Last Ticket	12](#heading)

[Cancel Ticket View	15](#cancel-ticket-view)

[Winner Ticket View	17](#winner-ticket-view)

[Sold Tickets	19](#sold-tickets)

[Get Data	21](#get-data)

[**Actions	24**](#actions)

[Pay Tickets	24](#pay-tickets)

[Copy Tickets	25](#copy-tickets)

[Cancel a Ticket	26](#cancel-a-ticket)

[Revert a Ticket	27](#revert-a-ticket)

[Create a Ticket	27](#create-a-ticket)

[**Reports	30**](#reports)

[Report Per Period	30](#report-per-period)

[Results Report	32](#results-report)

[**Kiosk	36**](#kiosk)

[Valid Plays	37](#valid-plays)

[Hour	38](#hour)

[Draw	39](#draw)

[Products	42](#products)

Welcome to the **Grupo Banklot** developer portal. Here you will find a reference for how to integrate **Grupo Banklot** into your existing applications and workflows using our [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) [HTTPS](https://en.wikipedia.org/wiki/HTTPS)\-based API. Our API uses standard [HTTP verbs](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods) to specify the intent of the operation, and HTTP [status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) to indicate the response to those operations. Security tokens are issued on login which are included as [HTTP headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields).

Use the language selector at the top to show examples in your language of choice, and use the version selector within the code sample for each API to see a sample request/response for that particular version.

# **EndPoints** {#endpoints}

API calls to the **Grupo Banklot** portal use the following base URL:  
[https://staging.loterias24.com/](https://admin.staging.loterias24.com/)  
API calls listed below will provide the URL that must be appended to this endpoint when making requests.

## 

# **Verbs** {#verbs}

The following HTTP verbs are used. A description of how each is used is shown. Please refer to each API individually for the appropriate syntax for resource creation or update as they can use one of PUT, POST, or PATCH.

* GET \- retrieve a resource  
* PUT \- update a resource  
* PATCH \- update a resource  
* POST \- create a resource  
* DELETE \- delete a resource

# **Status Codes** {#status-codes}

The status codes returned by the API include the following:

* 200 \- OK \- the request was successful  
* 201 \- Created \- the resource was created  
* 204 \- No Content \- the request was successful, but there is no data to return  
* 301 \- Moved Permanently \- the resource can be accessed through another URL  
* 400 \- Bad Request \- there is an issue with the request you submitted  
* 403 \- Forbidden \- authentication failure, or deprecated API version  
* 404 \- Not Found \- resource not found  
* 500 \- Internal Server Error \- there's an error on our side, email us\!

# **Authentication** {#authentication}

## 	**Login** {#login}

Authentication involves the use of a single API. However, multiple authentication and administrative APIs should be used in succession to retrieve the appropriate metadata to use to query the API.

1. To login with credentials, call POST /auth/login. The request body should include the following key-value pairs.  
   **Endpoint**: /auth/login  
   **Method: POST**  
   **Headers:**  
   * **Content-Type: application/json**   
   * **Request Body:**

| {  "email": "username@banklot.net",  "password": "\*\*\*\*\*\*" } |
| :---- |

   

2. Response:  
   * Retrieves a token and sets it in the environment variable for future requests.  
3. Event Script:  
   *  Parses the response body and sets the token in the environment

**IMPORTANT**  *Upon a successful response, extract the x\_auth\_token value from the JSON response. This value is the security token which must be included in subsequent API calls using the x-auth-token header.*

## **Logout** {#logout}

To log out of the existing session, call **GET /auth/logout** with the **x-auth-token** set.

# **Queries** {#queries}

## **Ticket View** {#ticket-view}

**Endpoint**: **/user/ticket**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:**

**Request:**

| {     "ticket\_number": 32426439,     "date": "2024-10-22" }  |
| :---- |

**Response:**

| {     "status": 201,     "response": {         "ticket\_number": 32426439,         "pin\_number": 76479163,         "num\_wagers": 6,         "entity\_id": 213,         "parent\_id": 212,         "entity\_name": "test-1",         "parent\_name": "test",         "created\_at": 1729587036,         "wagers": \[             {                 "amount": 3,                 "current\_event\_id": 23336,                 "event\_id": 23173,                 "event\_name": "ASTRO ZAMORANO",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:00 pm",                 "status": "sold",                 "wager": "444-ARI"             },             {                 "amount": 3,                 "current\_event\_id": 23336,                 "event\_id": 23173,                 "event\_name": "ASTRO ZAMORANO",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:00 pm",                 "status": "sold",                 "wager": "444-CAN"             },             {                 "amount": 3,                 "current\_event\_id": 23336,                 "event\_id": 23173,                 "event\_name": "ASTRO ZAMORANO",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:00 pm",                 "status": "sold",                 "wager": "444-ACU"             },             {                 "amount": 3,                 "current\_event\_id": 23310,                 "event\_id": 23147,                 "event\_name": "ZODÍACO DEL ZULIA",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:45 pm",                 "status": "sold",                 "wager": "444-ARI"             },             {                 "amount": 3,                 "current\_event\_id": 23310,                 "event\_id": 23147,                 "event\_name": "ZODÍACO DEL ZULIA",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:45 pm",                 "status": "sold",                 "wager": "444-CAN"             },             {                 "amount": 3,                 "current\_event\_id": 23310,                 "event\_id": 23147,                 "event\_name": "ZODÍACO DEL ZULIA",                 "game\_id": 3,                 "list\_id": 3,                 "p\_event\_time": "12:45 pm",                 "status": "sold",                 "wager": "444-ACU"             }         \],         "amount": 18     } } |
| :---- |

## **View Printed Ticket** {#view-printed-ticket}

**Endpoint**: **/user/ticket/image/f3f30cdb-2165-487b-bfd0-c990b7ab62c1**  
**Method: GET**  
**Headers:**

* **Content-Type: application/json** 

**Request:** Ticket must have the uuid format as part of the URL not the body.

**Response:**

| ![][image1] |
| :---- |

##   {#heading}

## **View Last Ticket**

**Endpoint**: **/user/ticket/last**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** No body is required.

**Response**:

| {     "status": 202,     "response": {         "ticket\_number": 10063292,         "pin\_number": 38037945,         "num\_wagers": 3,         "entity\_id": 213,         "parent\_id": 212,         "entity\_name": "test-1",         "parent\_name": "test",         "created\_at": 1729664000,         "wagers": \[             {                 "amount": 22,                 "current\_event\_id": 23301,                 "event\_id": 23301,                 "event\_name": "JUNGLA MILLONARIA",                 "game\_id": 5,                 "list\_id": null,                 "p\_event\_time": "09:00 am",                 "status": "sold",                 "wager": "0"             },             {                 "amount": 22,                 "current\_event\_id": 23301,                 "event\_id": 23301,                 "event\_name": "JUNGLA MILLONARIA",                 "game\_id": 5,                 "list\_id": null,                 "p\_event\_time": "09:00 am",                 "status": "sold",                 "wager": "1"             },             {                 "amount": 22,                 "current\_event\_id": 23301,                 "event\_id": 23301,                 "event\_name": "JUNGLA MILLONARIA",                 "game\_id": 5,                 "list\_id": null,                 "p\_event\_time": "09:00 am",                 "status": "sold",                 "wager": "2"             }         \],         "amount": 66     } } |
| :---- |

## **Cancel Ticket View** {#cancel-ticket-view}

**Endpoint**: **/user/ticket/**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the date time range with the status.

**Request:** Must specified the date time range

| {     "filter": {         "between\_created\_at": \[             "2024-06-05T04:00:00.000Z",             "2024-10-23T03:59:59.999Z"         \],         "status": "canceled"     },     "sort": {         "created\_at": 1     } } |
| :---- |

**Response**:

| {     "status": 200,     "response": \[         {             "id": "639a1521-49b9-4876-a36c-36c621593930",             "ticket\_number": 13239361,             "created\_at": 1721660369,             "user\_id": 864,             "email": "taquilla@banklot.net",             "status": "canceled",             "total": 6,             "prize": 0,             "entity\_id": 213,             "parent\_id": 212,             "entity\_name": "test-1",             "parent\_name": "test"         },        \],    } |
| :---- |

## **Winner Ticket View** {#winner-ticket-view}

**Endpoint**: **/user/ticket/**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the date time range with the status

**Request:**

| {     "filter": {         "between\_created\_at": \[             "2024-10-01T04:00:00.000Z",             "2024-10-23T03:59:59.999Z"         \],         "status": "winner"     },     "sort": {         "created\_at": 1     } } |
| :---- |

**Response:**

|     "status": 200,     "response": \[         {             "id": "af681029-87a2-4834-b7f9-56d88ee3a74e",             "ticket\_number": 23315522,             "created\_at": 1728066656,             "user\_id": 864,             "email": "taquilla@banklot.net",             "status": "winner",             "total": 33,             "prize": 330,             "entity\_id": 213,             "parent\_id": 212,             "entity\_name": "test-1",             "parent\_name": "test"         },  |
| :---- |

## **Sold Tickets** {#sold-tickets}

**Endpoint**: **/user/ticket/**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the date time range with the transaction\_type

**Request:**

| {   "filter": {     "between\_created\_at": \[       "2024-08-28T04:00:00.000Z",       "2024-08-29T03:59:59.999Z"     \],     "transaction\_type": "wager"   },   "order\_by": \[     {       "name": "created\_at",       "value": "desc"     }   \] } |
| :---- |

**Response:**

| {     "status": 200,     "response": \[         {             "id": "16baefc2-5c3e-4f17-a26c-c19808e22655",             "ticket\_number": 30213646,             "created\_at": 1724896556,             "user\_id": 864,             "email": "taquilla@banklot.net",             "status": "sold",             "total": 10,             "prize": 0,             "entity\_id": 213,             "parent\_id": 212,             "entity\_name": "test-1",             "parent\_name": "test"         }, \], } |
| :---- |

## **Get Data** {#get-data}

**Endpoint**: **/gaming/get-data**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:**

**Response:**

| {     "status": 200,     "response": {         "entity\_id": 213,         "name": "test-1",         "status": "active",         "games": \[             "animalitos77",             "animalitos",             "tripleta",             "lottery"         \],         "entity\_data": {             "address1": "",             "address2": "",             "city": "",             "municipality": 1,             "rif": "1234",             "seconds\_to\_cancel": 180,             "state": 3,             "ticket\_expiration\_days": 3,             "ticket\_footer": "123",             "ticket\_header": "123",             "time\_zone": "America/Caracas"         },         "game\_data": \[             {                 "amount\_multiple": 1,                 "commission": 10,                 "game\_id": 1,                 "max\_bet": 99,                 "max\_permutations": 6,                 "max\_sequence\_size": 10,                 "max\_sequences": 2,                 "min\_bet": 1,                 "product\_id": 1,                 "ticket\_max\_wagers": 100             },             {                 "amount\_multiple": 1,                 "commission": 10,                 "game\_id": 1,                 "max\_bet": 99,                 "max\_permutations": 6,                 "max\_sequence\_size": 10,                 "max\_sequences": 2,                 "min\_bet": 1,                 "product\_id": 2,                 "ticket\_max\_wagers": 100             },             {                 "amount\_multiple": 1,                 "commission": 10,                 "game\_id": 1,                 "max\_bet": 99,                 "max\_permutations": 6,                 "max\_sequence\_size": 10,                 "max\_sequences": 2,                 "min\_bet": 1,                 "product\_id": 3,                 "ticket\_max\_wagers": 100             },  |
| :---- |

# **Actions** {#actions}

## **Pay Tickets** {#pay-tickets}

**Endpoint**: **/user/ticket/pay**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the ticket number, pin\_number and date.

**Request:**

| {   "ticket\_number": 10653459,   "pin\_number": 84038675,   "date": "2024-09-16"   } |
| :---- |

**Response:**

| {     "status": 200,     "error": "not a winner" } |
| :---- |

## **Copy Tickets** {#copy-tickets}

**Endpoint**: **/user/ticket/copy**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the ticket number and date. 

**Request:**

| {   "ticket\_number": 71998218,   "date": "2024-09-17"   } |
| :---- |

**Response:**

| {     "status": 201,     "response": {         "ticket\_uuid": "362a5a41-2ac4-4c8f-a8f7-a907f86e4426",         "ticket\_number": 71998218,         "num\_wagers": 1,         "wagers": \[             {                 "amount": 5,                 "event\_id": 23335,                 "game\_id": 1,                 "old\_event\_id": 18748,                 "wager": "001" |
| :---- |

## **Cancel a Ticket** {#cancel-a-ticket}

**Endpoint**: **/user/ticket/cancel**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the ticket number

**Request:**

| {   "ticket\_number": 18712010 } |
| :---- |

**Response:**

| {     "status": 400,     "error": "no rows in result set" } |
| :---- |

## **Revert a Ticket** {#revert-a-ticket}

**Endpoint**: **/user/ticket/revert**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the ticket number

**Request:**

| {   "ticket\_number": 71998218 } |
| :---- |

**Response:**

| {     "status": 401,     "error": "ticket already rejected by user" } |
| :---- |

## **Create a Ticket** {#create-a-ticket}

**Endpoint**: **/user/ticket/create**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the amount, event\_id, game\_id, and the wager.

**Request:**

| {     "ticket": {         "wagers":             \[                 {                     "amount": 2000,                     "event\_id": 18859,                     "game\_id": 1,                     "wager": "341"                 },                 {                     "amount": 2000,                     "event\_id": 18859,                     "game\_id": 1,                     "wager": "000"                 }             \]     }} |
| :---- |

**Response:**

| {     "status": 409,     "error": "events are not open. closed events: \[18859\]" } |
| :---- |

# **Reports** {#reports}

## **Report Per Period** {#report-per-period}

**Endpoint**: **/gaming/reports**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the date time range, group and category.

**Request:**

| {   "between\_timestamp": \[     "2024-06-27T04:00:00.000Z",     "2024-06-28T03:59:59.999Z"   \],   "group": "user",  "category": "lottery"  } |
| :---- |

**Response:**

| {     "status": 200,     "total": {         "agency": 0,         "balance": 0,         "parent\_balance": 0,         "prize": 0,         "sale": 0     } } |
| :---- |

## **Results Report** {#results-report}

**Endpoint**: **/gaming/result/0**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain the date time range.

**Request:**

| {   "filter": {     "between\_created\_at": \[       "2024-08-18T04:00:00.000Z",       "2024-09-18T03:59:59.999Z"     \]   },   "order\_by": \[     {       "name": "event\_timestamp",       "value": "desc"     }   \] } |
| :---- |

**Response:**

| {     "status": 200,     "response": \[         {             "id": 18697,             "game\_product\_id": 6,             "name": "JUNGLA MILLONARIA",             "event\_time": "16:00",             "event\_time\_utc": "20:00",             "closing\_timestamp": {                 "seconds": 1729713300             },             "game\_category": "animalitos",             "status": "result",             "event\_timestamp": {                 "seconds": 1726603200             },             "display\_order": 20,             "main\_result": "5",             "event\_status": "closed",             "result\_created\_at": {                 "seconds": 1726545660,                 "nanos": 192719000             }         },         {             "id": 18732,             "game\_product\_id": 1,             "name": "TRIPLE ZAMORANO",             "event\_time": "16:00",             "event\_time\_utc": "20:00",             "closing\_timestamp": {                 "seconds": 1729713300             },             "game\_category": "lottery",             "status": "result",             "event\_timestamp": {                 "seconds": 1726603200             },             "display\_order": 19,             "list": "C",             "list\_id": 3,             "main\_result": "000-ACU",             "event\_status": "closed",             "zodiac": true,             "result\_created\_at": {                 "seconds": 1726545660,                 "nanos": 192719000             }         },         {             "id": 18731,             "game\_product\_id": 1,             "name": "TRIPLE ZAMORANO",             "event\_time": "16:00",             "event\_time\_utc": "20:00",             "closing\_timestamp": {                 "seconds": 1729713300             },             "game\_category": "lottery",             "status": "result",             "event\_timestamp": {                 "seconds": 1726603200             },             "display\_order": 19,             "list": "A",             "list\_id": 1,             "main\_result": "000",             "event\_status": "closed",             "result\_created\_at": {                 "seconds": 1726545660,                 "nanos": 192719000             }         },         {             "id": 18694,             "game\_product\_id": 6,             "name": "JUNGLA MILLONARIA",             "event\_time": "15:00",             "event\_time\_utc": "19:00",             "closing\_timestamp": {                 "seconds": 1729709700             },             "game\_category": "animalitos",             "status": "result",             "event\_timestamp": {                 "seconds": 1726599600             },             "display\_order": 17,             "main\_result": "2",             "event\_status": "closed",             "result\_created\_at": {                 "seconds": 1726545660,                 "nanos": 192719000             }         },  |
| :---- |

# **Kiosk** {#kiosk}

## **Valid Plays** {#valid-plays}

**Endpoint**:**/gaming/inventory/template**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** No body is required. 

**Response:**

| {     "status": 200,     "response": \[         {             "game\_id": 1,             "wager": "001",             "code": "001"         },         {             "game\_id": 1,             "wager": "002",             "code": "002"         }, |
| :---- |

## **Hour** {#hour}

**Endpoint**: **/gaming/time**  
**Method: GET**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:**

**Request:**

| {   "filter": {     "between\_created\_at": \[       "2024-04-21",       "2024-04-21"     \]   },   "sort": {     "event\_timestamp": "desc"   } } |
| :---- |

**Response:**

|  |
| :---- |

## **Draw** {#draw}

**Endpoint**:**/gaming/events/search/kiosk**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** Must contain date time range, game category and status.

**Request:**

| {     "filter": {                 "between\_created\_at": \[             "2024-06-05T04:00:00.000Z",             "2024-06-06T03:59:59.999Z"         \],         "game\_category": "lottery",          "status": "open"     },     "sort": {         "game\_category": "desc",         "event\_timestamp": "desc",         "display\_order": "0"     } } |
| :---- |

**Response:**

| {     "status": 201,     "total": 0 } |
| :---- |

## **Products** {#products}

**Endpoint:/gaming/products/search**  
**Method: POST**  
**Headers:**

* **Content-Type: application/json**   
  * **Request Body:** No body parameters are required.

**Response:**

| {     "status": 201,     "response": \[         {             "id": 17,             "name": "TRIPLE DORADO",             "lottery": "LOTERIA DE GUAYANA",             "lottery\_id": 22,             "status": "active",             "quota": 1000000,             "game\_category": "lottery",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23286,                     "event\_time": "14:00:00",                     "next\_event\_date": "2024-10-24",                     "next\_event\_time": "12:00:00"                 }             \]         },         {             "id": 30,             "name": "LOTTO REY",             "lottery": "LOTERIA DE MARGARITA",             "lottery\_id": 24,             "status": "active",             "quota": 1000000,             "game\_category": "animalitos",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23431,                     "event\_time": "13:30:00",                     "next\_event\_date": "2024-10-24",                     "next\_event\_time": "11:30:00"                 }             \]         },         {             "id": 18,             "name": "GUACHARO ACTIVO",             "lottery": "LOTERÍA DE ORIENTE",             "lottery\_id": 23,             "status": "active",             "quota": 1000000,             "game\_category": "animalitos77",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23346,                     "event\_time": "14:00:00",                     "next\_event\_date": "2024-10-24",                     "next\_event\_time": "12:00:00"                 }             \]         },         {             "id": 27,             "name": "TRIPLE CHANCE",             "lottery": "LOTERÍA DE ORIENTE",             "lottery\_id": 23,             "status": "active",             "quota": 1000000,             "game\_category": "lottery",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23366,                     "event\_time": "16:30:00",                     "next\_event\_date": "2024-10-23",                     "next\_event\_time": null                 }             \]         },         {             "id": 2,             "name": "TRIPLE ZULIA",             "lottery": "LOTERÍA DEL ZÚLIA",             "lottery\_id": 1,             "status": "active",             "quota": 1000000,             "game\_category": "lottery",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23311,                     "event\_time": "16:45:00",                     "next\_event\_date": "2024-10-23",                     "next\_event\_time": null                 }             \]         },         {             "id": 1,             "name": "TRIPLE ZAMORANO",             "lottery": "LOTERÍA DEL ZÚLIA",             "lottery\_id": 1,             "status": "active",             "quota": 100,             "game\_category": "lottery",             "lottery\_status": "active",             "data": \[                 {                     "event\_date": "2024-10-23",                     "event\_id": 23316,                     "event\_time": "16:00:00",                     "next\_event\_date": "2024-10-23",                     "next\_event\_time": null                 }             \]         },  |
| :---- |

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAM4AAAC5CAIAAADvWpfqAAA6hklEQVR4Xu1debxNVf8+4d6KyJTpytBAGaIfqTSI3gqFCilNildFadCnREW9UkRR6K2EQtGk8tabUEmpSIYkXFy66lKpuNcdzrnnrN/j+7z72zp7n3vcqUPZzx/7s/baa6/hu571XfNaAePDR0IQcFv48PHnwKeajwTBp5qPBCGKajk5OcFgEIZQKESb3377TV9//PHH3NxcmF1udu/eTRtgz549NBDhcFjN+ETfbEQiEfv1l19+yczMzMvLgxlh4UlzVlYWXmGGD4gkHSNQxsHlyd8bKnbF3r17ITQY+IRY8vPz9StER4PmEWA7UBtmFv2nV0Zy0OWYrxoNV3wYHChhnBxUxNBq/Pn333+3LfkbMhWZjcCYu7TcsWMHCRERrFixAqmiA9jTNzrwiomgnzS72AM5GikDjtv/QR08/fTT0V/+/li0aFFKSgoMc+bMCQQChx9++Icffjh+/Phx48YZEcgTTzxx9NFHly1bFl9Hjx6NJ+y//PLLIUOGwNC2bdto//6Hnj17Vq5c+auvvlKv8OPPP/+M5xFHHIEnQilXrhwNyJeAAKF369bNDg5ZCYOtZQg31eBu4sSJzz33nBF+KDGRtSQftQ494lfwQIliqyKYs7Oz+Ur3P/30E50RpCYMn332GW2g1YzDcvipJRI499xzadACB/z6669qPnQACXTt2hWGN998c8yYMUY48e9///v555+H+aWXXpo8eXJSUhJUgBExgh/t27dftWrV8OHDYXPYYYfhR9tDYMmSJb1794bhv//9r3oFb+HJzTffzPIPht122220f/nll2E46qijkIPIaDs4OjDRddo+S/uFOO+883r06EHz/fff/+ijj4IB8PGSSy7BzzNmzDDi1/Llyx9++GGYZ82atWbNmvfffx8Zr5zbtWsXnitXrkQJU5vTTjuNZgJRpLrasmULSIn0dO7cGa9IKhzXqlULnEOSYA9n/Be/IOgqVaqUKVNG/VENdygAPIM0kEcwz58/n2rmWQEVxPTp00E1WFatWhVPyBDPatWqbdq0adSoUcipmTNnQrbearFmzZpt2rSBWb2CkJGnDOKBBx5YsGCBKLLAddddZ4RJ0GSsee3gkB0wuJpSJibVKlasCN9R3SJVTz755NixY2mP/+E1ygT9oiXcqJlAwFRmqamp9evXh4IFV7Qp4AK8omOCKUER4evIkSOhmeEANTKCVmfG0W3eivVvD4gxPT29efPmME+bNu2pp54yIjfoIfLjhRdeANs0UyAiZEFaWtpVV1314IMPnnrqqfhkF1QbEDUcq1dwiTJ/5ZVXUqvNmzdv4MCBqH8RAVZcIAM/2cGhbkW+aytLEcUSfAZ56Uvr1q3x3L59u5EWPX5DXQ4zVDd8V6+hZsDFxYsXv/rqq0YEgd9RUSJIlBI8r776arpEg+yyyy6jmWDFCt+guvr37w8bOECl2aVLF3y68cYb4Tlqczb4WrZsCXllZGQoNdnOtSvZQwRoddWrVw/6A9qrY8eOoALaWEbyG2Jk1uA5ePDgxx57DE1nFFfaoBZKTk6GGWTS2oZYuHBh7dq18TtJDMc33XRTs2bNUOGcccYZd9xxB3z74IMPbrnlFhRy0HHdunXIF+odV3B4RbWDfLE7Ivvc2C/Azp07jXALuQvFhgoYz0qVKoGFrMhc7o1ktqunGZHeg/FoHbuZZaQMGSErHCPe+Ap/GD8tEOqDrfBZGIiYyvJQAORmpx0yYdsXoKahtCnkbIEKE4onZlYS9Mq2yXGGJoDNmzezrwb/2dMk7OBiwk01Ao0zNvCbNm0K5m7cuNGb5UiPnVTYazAcmDDSwEe0mHLjtPoVjDGBSMM3hGL3kOmhi6BGggbs3w8dgASQLdIOg0oAglKS0cDqRX+hxAjae9tqxim3Nl+JHIFmDclAOsI3to40OKgnfnIhBtW0SmIeu+Kk8DKAodpRJBiw+kOD11kcMBkRkbKJlkvIGeeLo94Ylp0QVZ9aWBlJm+g+ShdRVGNGsm2kQvcqjzxn8MILZqeLnXnOoEkc7bpfMG70x0UIlo0ca8zFHivGj+QT+0R2ckLRitnVtvBRunBrNW8f1Vupw4Zdbpe9PW3gAvKbzQUd4CgG8COZoT7YA3UFsZ/2rNOhulwxZANRVWxMze+jVOCm2hVXXJGUlCRjDgFmZLly5VxuoBhg6c1aNsXwu7dyRMe2SZMmxuk/I7+9vxcE1P2rVq1C12nAgAH4a9u2bfCkb9++6qBOnTpgOXrgZcuWrVatGtyAQLNnz65Ro8Z7771nZKQXrx999BHM6LLB/scff4T52muvRV+Jw5VE4WPlo6hwU41o2LChEbkjU9H9DMq02qOPPorXadOmGWEMlERKSsqLL74IhVGzZs2rrrqK9oRxqiq23vAv/KEDDpI1atSoZcuW+Hr33Xcjv9Hzjd9OAo/p7e23344niYsYomzAHv4MHDiQOumII47Ak/3/fIGRcOfPn484s4uNbvznn38+cuRIcLRu3boFKWMfpYgCqcbyzakuIzndvHlzZJVOWbRt21ZnDvAcNGgQdA9fqQ7ZuqI/w4cPX7du3fXXX4+voBS4ha9vvfXWxx9/DEtwEURE9bp06VKORNsgBfHjscceCzP5xEC3bNkyePDgww8/PFMAm9GjRw8bNiwtLQ0ObrjhhksvvRQB1a5dG86WLFkC9XbrrbeWL1/+u+++Y9LgAE/2f42nlemjFFEg1YzDFY4sQ5lxug2ZnS/zqT179kQtBn0AM5j02GOPrVy5Eg6QkfzRSD+AeuXhhx/esGFDhQoVSBHqIThDxTpnzpyQNSYcB1BFpB0qUxAOzUr8VbFiRTz79OlD++7du8MNOgrUsog8tBdniw877DD6kyuzW+AW+xP169fnmHNQ8Ed4PkoVsTMYVOPA7EMPPYRcmTJlCrIH2TZkyBBkJxo65ArqQeRQ796927Rp07Rp06Cs6oF+Aguhw4zVyoY/27dvh9IipTjLBD0UkTmuHj16tGrVyshc7znnnPNHPBwg0KFDh8Il/EfNCxqhGkUQuTKMCXtw+rjjjrvjjjvAORQAkBiWaJZRRyKqUHVvv/02gkNj7vTTT7/xxhuN1MLQiBxMN9aqJB9/BmJTzYePUodPNR8Jgk81HwmCTzUfCYJPNR8JQhTVdu/ezbkj7yIwdM2yZYmi2uzdu1cHNQj0RtUmLNi1axfHq3SmXLF161Yj3tr22bIWl8iRRXacSvKHu/4GcGs1ZvyWLVu4jBFEady4sbHWBYGFBU0UcpUbnHEF+urVq5999tmlS5eqg3bt2tkToEOGDAGHunfvnpGRwdXuCDQg8xAwp6enT506ddmyZTD36NEDnhe0/8LHXwJRVLNnAMuWLcsxUo6BQeEtX748OTmZ1CEbXMoGr/glMzPz1ltvhT4jR3/55RdqqU8++cRYizJ0pxN8Bv/q1KlDc7ly5Tju36ZNG12nBMWWlpbWrVs3vvr4KyKKajpdWLly5V9//ZV84mgtKLJmzRpUcGAbxzlRu7kmp6nSPv/8c34tX748eHbTTTcZYdjkyZPVJajTokUL/v7BBx9UqVKFyozjsRy1P/zwwzdt2mTPU1144YVq9vGXg7sCNcIYW10FZNaSG+Z27tyJV11+qW4IuqEyAy655BIjv+gWOl2hBJfff/89zUZ4efPNNxuZP6AS3bFjh/5ON7/99luFChX0Fx9/OURRTRthbP5Dh9WtWzcg20ppSa3DjXcxgU+TJk0yzn6W6tWrP/fccyAWWni6JhE85rwQ0bRp0wsuuIBmTigZIaX+DlLOnDnzqKOOihOuj4Mfbq3GZjtrTK0f2diCyuE5Bnmy5cR7KgL+YrfROFvpqc/yZduBtzMBT1R9anchJKvjqf/4u71XwsdfF26qGaePySwH8mWTAtthoBHJEZblh2y02T/SgK8///wzmZone/WM1JLKtnxn5zoM1KAaEC3pCX/Xpys4H38tRFGNeQl1Rc0UdjYP2yAz0tPTXfYuUEtBOdldh2Jzhf1W/s4owX++qv96yEjI2TFAytJ9vrUDlr7RvWpTlI082YWgHnoXpqs0dOm5dqi1k8Rec8TZSs1A1RlfvQr+UEAMrcYszJV1aSbWNhYqJNcBHMbKTluUyDy6jHjW9RcedjclV0Az2UCNyzoXYSF6tOGTLhE0ow1KGSFNUJYMefmEWttmqkIDVQTlFBxXomx+42uOLIODh/ydX9kwKLY0/qKIopr2BvTV1kkKSBCdQbsLSajW8bauYOmlbEmAsLS+Djn782KChIChc+fOZJ4O1zF1rqkRPXlEO7+Ey5kyj57YEdDk0x8tft7WrZe+f2NEUS1XllOzZrFVggvaT/SCcv+///s/iBv91rCz0pWVmuZxUYEuKpjatWtXZN4NN9wAf8Ab1Z0nn3wyS8VNN93EjQVwlpKS8t13361evZqqC9nM5uNLL70Ew4svvghn9erVW758OUePr7zySiS8U6dOxjnmzZVGCKd169ZwM3To0LPPPlvtERYcd+nSxUgyUahOOumkTZs2rVmzxghfOQUHoXXv3h0R4CFCXm36t0eUNLWfqN3PBQsWIM9YGb388stVq1Z97733YC5TpsyZZ55ZpUoVIw0y5FbLli3pCb7y4AYdgePRCpMnT65cuTJVJj6deOKJ99xzD8zwEK/MGDjr1asX/XEBVNu4cSNIwEzKyMgwjsZatWpVxOnHkB/QTNu3b3/jjTeaNm1KfoMc+U4XBIa6desigZs3b162bNlxxx2n3R3VZKAONLfdbkPhmTp16uLFi88///xx48Zxe1iPHj127doF+bRr1w5+GilsP/zwA6jMjTbt27eHeyOqbvr06fBnzpw5+QUclvP3RmzlZERkIBxPPoPUIJ20tDR+gqLi4D7KrhFeImvJADi7/PLL82V0A27Y7iG9vv32W+PsWlCFoZrpqKOOMkLKmEemIawff/xxzJgxCJqe8wQeUAQZmScbPF1Ug/pJTU3VgDiXygy+6KKLaLl+/Xq4gZ/U39B2I0eOBIc4nszRRGP1ZmbOnPnNN9/UrFlzypQpqqERH7YNEHkwG4YNGzZAiXLLFn7h9AmChoPjjz8+YvW1Dym4qcbWA5/IUfLDiLhh1ioV6i0iB0MYOYVwx44dSpHXXnuNBmq1PDldAWX666+/NjKzCZdkALNw1KhRMJQvX55/eRs0sIHmmDVrFnQSCA0qPPPMM8apg959910jlLWpBvAEpFtuucXILL7SpWPHjtpF6Nevn3FmY+EtVBGpTyWnXmk7jFtiIZyKFSvmOgcValUIZ1RsqOLx7N+/PwsnXI4fP14DNcLOQ51qFDSfITlLAVoNteTHH38M6aD6gPQ/+uijfb9JNjAP3nrrrUqVKnGS4K677iIdIUpUsnaLZN68edyTB/ORRx7JtjOCQPaccMIJelLXKaecor8QzHX4lpycnCu7aQIC6K3hw4cbiapNNZYTKB5U/fnSkELNhSdjyx1WPMINTYL69etPmzYN8YTnPD3OSLqUauREvuzvQpyh0sAhpguM5JF6ABp5SAXNc+fOrVGjBgxotNG300477YsvvtBOgE+1UsCgQYPyCj7Ro9RRmOBQbbk6jz4OCEqTanFGHP4MFD44KCEdwfFxoFCaVEP9xWqx2IMaRUJhgvMZdvCgNKlG6EqhxGC/wXHyIH4l6yMBiE01bdxoRrKvzl4n2++c2wnK9A6Vh9ZoOoSh0IEr43xl01sdsLugHqob7fN6cUgNtf8N4O6BgkkLFiwIykkctOQAm5GM1/rInmUi81q0aKE2xpmcYU9t165ddG//hbAqV65MdoLZMWu6HGdOXcHXM844g3dEcCTFduDjoIWbakamlYwzgKkks9tDnLliHm/evFltVKtxu4C+2p+MhMJ1EBUqVIBLBgEfWMfZK3X1Fxt33nmncYbfyN2YNPVxsMFdgebKqY7Tpk0LyFh/2bJlN23a9MgjjxjZ7/TTTz+98sordBmUMUkyA+ypXr26cc424xra888/H3SsX7++EW3Uu3dv8JWzh126dElNTeUZR9yaxWmc+fPnI9ABAwZwViBmAwtRqlmzJicxjfAspjMfBxvcVDNSnV100UVc489qlIonJMfLJyUlafuJ1RlyWs/Z45Pa8fTTT0fV2b59e1ajvXr1gqbUyxlgyXHUvn37BuQWI9gsWbLkpJNO4qUy5JC3dwnHsORaICOM9zYNfRyEiKKa3TA68sgjjaiQoEwHGVE8O3fuXLRokboh7Gmcjh07gl5c5lC7dm24V5XzzjvvcFISvkHhgS6oQMGnzz//fNWqVVSiUJn4hdfPhGVViLdyfO2115YuXao3b/j4qyCKatnWyg7akGTaJWTP1J5u0r6qdiNCzuojHpkGWtgMxr+cLaWlrZAyMjLQAnO12LxgG1FdmlgdXh8HIWJUoMZpkjML85zD2F3IlzU5yPLJkydXrFjxhx9+UA1Eorz++uvJycm6jMIFu4EVFtAMD0nf+GMZ7CxHPOcz+DhoEZtqPnyUOnyq+UgQfKr5SBB8qvlIEHyq+UgQfKr5SBB8qvlIEHyq+UgQ3FQrV67cvi0iPnwUBWXLlg1E79D2Iupzbm4uby/09334KBKynBOSvXPWihhMzPScZuXDRyERc8c4EUU1LoHkalvOS/rwURjoMjObTi7E0Gr+BLaPYiPmygzCTbUsuZvRWITjop0cOR8l07myPSMjg6oSdNZF2/yLdTbJTsuDH7kC40jqhx9+sNez2C3X+AW3FAExQtp6VoOrDaSb9bl0lJHnWcG6pAoO9londcaHrV90OSoSnuscs2cc/42z2r6oWeymGnDPPfcg4J49e6anp7/++uvvv/8+j9uA5ffff3/99dcbWSbE408AdD10eRlPeeHd2XEIfhAiIJeK0nzCCScg7UgFRMklogMHDjSSoqSkpCLJtxhgTh922GFcypUt1/cietu3b3/++eeRBRdffLGR8gAHFDJK/uzZs9evX08fatWqpUsP4wA6onPnzjQjXd99993cuXNXr169ZMkSI2coheRKYPBVab1t27ZPP/103rx5xcjiGFQbN24cDSkpKdwn0qhRI/1atWpVIwvaeLT7L7/8UqZMGVINEklNTYVh1apVuc6xWX92xpQKoDbsvjoEChtk7R65JMTIYZTIGCTwww8/jL+QroRQjVK7dm3QRQ/LQTRq1KgRkdPvUJ8gDmeffXbz5s35NVfuakIJIb3mz59fGLEjc7m2vkWLFihRxx13nBH2nHrqqUj+e++9Z5xLgo3wEsxTShQji6OoFpbjkmF46qmnZsyYgWAictYhNwQgtYiQnkCmkYClbjKwt9+FZemivh7kQHKo1YLOZgW+cqCRdy8PGzYMT17V/echU0CKa/3F4Svb8Oyzzy5YsEBXRCO23OQ2evRoPAcMGED7OJsXOULRtGlTeAIlihopKJtzobEogWrVqtFPVJ3wH9Ua81rVf5GyOIZWM+IF0sONUkb2w7G0QUVzg6dxToDCa0AOBaLl7bffDgXA06PgSZx0HlRACUEqdDn70KFDjWh3JAGyhqCRHxA0ty0ijVT8hSzNhQeEGZYd3XjyAiSY2UKC4uF2Cirgr776irIdP368cQ5LpIPTTjsNz3vvvZd+xqGCZlCuXGZ/2223kUYwcK8kshvRyJcD5Ohy8ODBVOqPP/54UbM4imrZgrPOOqtOnTqkVKtWrRh142y5a9as2Y4dO/b96TRuWM5Yn3755Zcwozo3cRN5EEILDGS3du3aKlWqoBrKkkMLkbvIdTRieG0DUt22bVuq/9JNI5s+kyZNot4iyZ588sljjjnGSGMc4R5xxBEfffQRbYxDLLhv164dsyMtLY16YdGiRVodxwcYwzrqlFNO4UFdxtmmSQ3HWguSgQGUaNKkCRSqKWLyo6hm709h3Uy1aTx74PKdTZrsh6qqY2rDclIkKV/qRf/PAJNmDz8y1UwOT0UNOfchaR9oT/RR+aUFb1sbPQCXjUIzJVvOtcgTGNHTNNhdSy80LGpT9Y0NU5rZGQ/J7iTQnSezGmf3ZOGzuECqEUrnsAzTaSVtwzuLpao1W+73dH09COHaSW+/amZA+nZL1DaXFhAEs9Nl/6scOq6SjBRwgr0NZmV8rQM3dACD9nWynbPYSVwjVGMWs2bX34uaxe62Gitml6UPH4WE1m9euLUa+vm2jQ8fRUJBJ62YmFoNmpNHtfvwUUiww2QKv7IjIhfVoNvCzrMPH4UEWpNxqk7CrdV8+PiT4FPNR4LgU81HguBTzUeC4FPNR4LgU81HguBTzUeC4FPNR4LgnpjiPG5Irs2jZVZW1l4BX73rDohg9IHznDPm2LFOBtvrV7lCRm3ynE0J+c4F8OqbLqlQ0NtCrpApJHTRAEMngs45wMaZwLYjzLlnxo2R0WUUtgB5nTzN8cG0wyv6acdEzQUNx9tHunKDCPzhX3FC50I019KMsEDTEjOl3gn+/SKGVuNEPUO69dZbA4HA8uXLuSiNCMuKexi6d+9uZF1UjRo1/vOf/5hoIqp7vkIWXHCnNklJSZDFKaec0qhRIwoFn4455pgtW7YwPdOnT2c0qlWrxhU+yLZVq1bBzTvvvGMK5n1RQX8eeeQRSnDlypXVq1d/9dVXjWSGnRNVq1ZFSuEsIyMDcTjxxBP1d13goAbYK+FYVuOvt6EbpjQ5OZkyQZJXr15tm+k47Kx5ZnBaJChzZE2OLKKErCpWrMhPXkDCZcqUufTSS132P//880cffVSvXr34KS0S3FSD1xMnTnzuuee4/hGvKBNBuRmduc4kkXDUTLxweMqUKWHnTqCwrAMGtyDo448/3kjUn3zyyZEjR2bL7cdLly799NNPYejTp48RWvfo0SPoLImDaCJyFXDdunUZaIUKFd5++23m+pgxY2Dz2GOP2cEx8qULptq2QcEzcp3tFVdcgaRBShDO3XffbZw46IoaHhKQI9vMjJM3BSkkG1mCwYMH66n7kIBe0gAz5EyzrTgnTZoE8dLMS3x1XX7NmjWNeOvVQ7o+z6X2IGcU9ddeew2JKiilxYCbasB5552HjKf5xhtv/Oc//2ksMUF8SAY108MPP6zqNyJr1Ox4wPzNN98YuWAa0W3Tpk3fvn3BzkqVKp177rnXX389tBoEqvQCHfk7PuG5bt06PFGIoQuh9s4555ws2SsGBgetTdEaXEmgFT3ykuUHPl9yySXGqhMRLpR3amoqCiEMzOYzzzyTy4/tjLz33ns3btw4d+5cSGn9+vVQlnBPfRCMvlnLhbCzVB+/V6lShXXiySefjOipWR1Te0GG8LN58+ZXXXUVhROQy3fHjh1rJPK8tITNG5e4WJbgnhfueoHUxU9pkRCDasj1cuXK7RHQpk6dOq6GEak2c+ZMPL/77jsj0smVLTTMG2beDTfcgCLCxhavF94rq/jpCVLYrFkzmqn8kPjrrrsO7mEAvQKyjhyFDwKFD8OGDcMnVKAIZevWrXZwJYdWQJTsBRdcEJGFzqo54KBly5YLFy5ESrm5qH379njWr1+fDkx06wqp05SiNixMPKld9BpnSIyVIGzUDOogd1zFDA4QHNegB+QKEShCOmAcQtbeEwWrLBi2b9/OmGc7i67xL7gFQ0EpLQbhoqiG/x944AEGhnoaaZs1axbife211xpn2TFLJxPAfRMgPtjAi39U1qg4WN3QEjWCkQS3bt2a/yIsZMCKFSuef/55NAu+/PJLOjZSOY4YMQL1OH6EXow4N7LffPPNRmoElIHatWvTZ/2rJGCiKHdI+b777rPXhzLPIA3U+2iYQjKINmyOPfZYRO/jjz+mszxntSrqARQ/NIMC0sxAbKk2WJl6s9wLKic7da6UkiX0CllGS8jWyK4+BNSvXz9t6iB1YGHMzsGgQYMQ1j333MN1ZkhCtrOBFCRbs2ZNQSm1/Cgs3FqNdfwe2bFit/4gejQPYUn1Zrd8s5wN8d7GDSKNr2jM2pZcnK5L1I34lim7g5BOuGdKmP0uMBrUNN7gSgj6xvJKcdutGdrrDm/mnK4E1NjCGfIVr95FgnQTv3jgX1JEmaFXHKmZ8gzJYn+XBHJkl422agh4hYTgk1cVsUVO2BFjSaOcY6a0GJJ3U40ADxgtPhEkaxN+/e2331xFE7GBZZ5cmZgrWxdZPjRtUNH5spQclMInra0Im9MuQRunFaivIdltQUFrcPq1eLB1GHVPxFq/r5HRgBA6Wxeu/qmJjjndqw2TFrMIKcJWkwBmOGZ81AwBgjeuQBEN0oJ00XiqV2zGxGS5ckj9DEkDxsjvBaXUzrJCwk01xlJLAMWkzECZZpK0Rtcf+aqJ1KZeRPqStjMj4laFQdbSK/VWm4kFZSQbal6fiw3NBoZo5wrlrhTRcFUxh6U5X4qRUaAAq7e22VWFqZRU5dBBjuxPATu9KlYRlN1QXssc2eRSiimNoppdJdE7LVK26DOdQ2Js3a7wFh1E1OWSda4dY8jCper4Ct/shrkRumcKaOkNrhjIlIXHNLtyUfOMLKfQmaP6i0uXlBboIZvqagYoEGYNY5Iv2p1/IVbZMuaiNplyloyXT/FJgySHRZWaWCl1qYDCwK3VEKEsgcteqxhGjqWELQP7K2OmqcqSrfpQYHQQJ4okH1WddsttQdiSQnVMgyu4kkAbYTBoxjB1qs8IfuKT7A8LbDelBdKF0dAWqrHUGPNeqaCfVCZae7hSobD/taE+lFZKo6jGeGtpAK655hp0YZYsWYI+NgyVKlViZ3BfXzwQ6Nq1K8z4CvPChQuVGTTQDcBmLDscSDCPMIIb+IlkNG3alCMdqCDgGD3q9PR0I5FBJ44C0p48yndqaurRRx/9/vvvu4IrOcaOHRuSJiD6j4iJXrJrLFWHftncuXNzBTAgJiyWpRUHRUCGx0AUJHzz5s1q3rRpU1BukdNKDZ9mz54dkGwywgkO+UIdBCSzIjLZZWLtnHv66aeRC23btnXZQw6zZs1CX7sUU+rWakgGOs869EwK2wWChYBp4PDHE088YeRUElfesyzytBzIBX4+9dRTQbkV/uuvv168eDEINHDgwBzZONOtWzdmJxJZs2ZNliHQjpZJSUkcw4PUJk+ebGRApBSpFpF+htbFTKOeIqbJ53B5r169+vTpg0AnTJhgZOyQX+mYBu10I3u0YQD/Xd0pLyAoOHvooYcqVKig/H7++efVPGPGDI0nm+1hZwaFocMHPWbh8MMPf+ONN2j2Siko0zOATi1EpLnC/hwkDJv9prTwcFMNdRNyvVOnTnwdMGDAlVdeGe1kHzhwDJKR6RyqiER3FY0oPDW3adPmsssug3RAtdatW/fv3x+G8uXLM1/hIdOJ51133YVO+Pfffw9ZgJQRGVc777zzTPQpc97gig2bakqOyy+/3ES3U1EGtmzZgrjpWT2dO3fmRJA6gz8jRoxYuXLl/PnzEW0ooYkTJ0I9hDyLBmKCozm8o5c2vHBczUwyYliuXDnUD3iSKNqmhAo0cpBPWGYCqLHYA7XrKyNUy5JDSRiW1pja1LvooovipLSoiKJavoxH8Jgntq74POGEE3LlsBB1ybOQeDoXqhtWOvRB3RirHCDqrIL3yOBkWPqYMJx44okMokGDBhQimQ3Lli1bQpkhqSE5UA7pf/zxx42c7GWc5nlhMq8wsKlmJMN4SgrqIPtYg7p163777bc//vgj4mbkSmekIiUlhT7QDVuxsEfMOY/JoqKexAccQ9lXrFgRT144TirYZpdv+GXr1q0shIg5MgsOkpOTITH4g4wbPny47d5Glsz1Kcmov6k+zjzzTOaCKSClRUVUpKH2dYgfTSg8oX7RTL7pppuYqVqVBISLV199NQJGNYd0NmrUiAo5LD1tJGDQoEGOx/tGpY3436JFi4CMXxs50iwtLe2FF15YtGjRxo0bOUUNPPjgg4MHD540aRKEtXbtWkSARzciwUZaS8hO1BF2cBpQ8WBTDZ6T0xFnaE1HCqAwoK5QKtatWweuN2vWDErrq6++snzaB5QW5P28efOQ38w2cM5uhBQEZjmCw188GoiNevtJ2GUM9IJ8ID0u0GDkly9fbiSb4PKSSy4JCfQXAgHdf//9Rs7EZBpRrqj5oFlR2NYJYqa0GIW8sKXNRyERkQZZnHGsQxY+1UoTOkhU7FrmbwyfaqWPwtSVhyB8qpUmgjJNudc5Rs+HDZ9qpQ+7q+5D4abaXjmkniONnCxyOTAyuMW2CMruzwLvrIX2UNijQVlnOwaeox+qv9MNkePcwqE22mmiJ6yY0NUKyoGGdnAlhD2zaZyhUW140cY40VAm6XSkkfTa7TO7u+caSvD2BL1AEOxv2kO+as6Wgx3pDyO2V8CvXBfESMKlzhDYgiW0y2+nVIGejUbVm9JiNEajqMb4gTrqL6/L6NWrl4neLMRlsX379kVs0CtGenRhMd2QBHjqaDU60pxcSk5Opo19LYN9CwdXXAad+ygynZPVGb0TTzwxPT2dWzNKsVW0Z8+ePn36BGXJyZVXXokUdenSxYiUWWyQH+jtf/LJJ9WrV0ckjWyu2b59+7Jly1wcokEH5JBnOm6yX4XHLIQPkBJLFF7POussNV944YV4bt26le7JJA4s88cvvvgCUZowYUJIxiNZZkhcFz+Qrn79+iFTeP68C3Xr1l2xYkX8lBYJbq1mZCrp9NNPp1mvyyDS0tJoqFy5MhhA8nHKMjU1NTf6zgQWI04oGZktaNWqlZHBns6dO7uuZbBv4ahVq1aurELT+yjwi17+gsTDEil3BVcS0IeILOSkDZi3adMmdZAny+/q1au3a9cuZDwHHZHBYB7NqqGhXaZOnQrLvbK0vUqVKtdccw13+qhXanaBvAFHL774YuTuXlkiBupQjdFsose0kOs7d+7s0KED5EmblJQUVQr2YC/HDvWVwL+w5OiaC99+++3ixYvjpLSoiEG1WbNmLVq0KGxdlwEbmz3GWf/OG2gIjiSFnVmLfDkmuF27dnxFFsITzlPhx7Vr1+ZEX8tg38LB2eVh1n0UsEeRgld2jtrBlS4QW6R01KhRTLXyD9Ho1KkT0sXxVeTT+vXroc6Vqfo7tEiDBg04p8IfadhvhJEu3m6hW0ueffZZ/QpzjuzVpbQjzgqrOXPmfPbZZ0YKLX4MOwv+OITLf/Gjt8VihKwPPvigbc8Ycmq/oJTGT0VMuKkG8tKXiRMnGic2KGHGqUAZGNQ7otKyZUs4vvPOO41MCUei70yAOKgFYblhwwZIPyKT5dDM9CRgXctg38KBgNasWaP3UdClEZUOUY4YMcLIkgRXcCVEtrMsjPrjpZdeUnvjMJuRefPNN7k9ifvK+vfv/4cvAviDtEOFB5z9AZrl2qIqCHDGhiNoqs2DoIDmvOhF3qAUCiE9BxHxlfGhe1YjyAUSVP8iWKtC/rqCnPZ5cso4903GT2mREEU1CEj1cNu2bVE6zz333EqVKul6FUqKVQMalXCP6hyaFkobitBEtwYCDmBu2LAh14HBW07nhWNdy7BH9jSAUqguebwqcho+wxPYb9u2DTJF865q1aoLFy50BVcSwFsU3HxZp25Eo5QRGE990bhxY9SPRij4yiuvHHvssczCiKVxUQy4+zIg12tAejBoM98migv0gVlOuZno9WR75OBYfSVQRyMj4DOaKKjpOPuH+sRIutCoRT0YjD57gIAl0oKAOFWthTYoM35o+bBVEyelRYJbq+ULaA4XML1I/cT5MgqCiwsox3xZ/wh5sTlMdtoa0TiJoTOVHS2N08NlNOg/7V2dKTs42pcELE5ML5qDDD1LZqNtZxQ0Y4Wnxp/80DJJhJzVHGFne7ZXtbhA9+qMSWbdYq82cx1DYSQsewmCZpz9l+YsoR0X5BGVN8ccGDozrqCU7jchXkRRDeHZc7qEnR5EJSQwVt/bpma+c2eCSwr6JJhh6ibb2eSTK4ul6FLrGmUSJU4G016Do4MSIsfZUaGrzZQ6QTkSwaWTXCxUQIZabIw4o0t4rkHEAXM3FL1z0zZnyaYyJRObkrnW0hsEAYZpBDJl65Dx9Bw1/uo4RxZ5qwP10JtS9bzwiKKaLno24heTh/D2yg2mmc6xJS4wcsonlyK0ZUTslku78p3rRdDmy7M2AhY0UZ0p97Cq52rIkSt5tIDSWVHJxw5QtrOJnJINSTlWlhhHPpoituqMSMCbzBJit9zMEpEz10ksNWfLVk0m3DgKhvG0GZNnteqy5VqgP3yPhlKKCDm3rtgK0k5gUcVLRFGNnuY7o5E5sneD2sVFIEQFJR7N5DgJIHJlSCIioI0a8gVGPGfRjDgVrg0EBDWjybOLnXEIYVPNOPoj5shkTDB1QeeUA1eJYogqa3Rc7FTnOrsDvTEvCXiPbLZsjKWNbf5dYJyourhiJM4oNqyjNm7c6PpKsG71qg/WXSz/2c4gsF23mpJrNTZNNGytp9UBvmpgdKaqlfYsi47zKGjkQgJIii7ttYfxke1cf8RdpYwYdSSlY+t5FyPjg+OfUFrePCOV1cxXeq6iCJb25mcTXerC0Ret2uEaSwvkSZuE9NLKAULjCKi9u7jw8ArES81CIopq6i8UyW233YbuDDov8+bNW7lypRFBT58+Hf3NHNkhqF0khI1OEM3r1q37/PPPR4wYgbShF4nEH3300SwWlAuzBL+jZ7527Vrj6TF400ZL/MIBCA5WQaCgV/ny5Vn4jMiUKwQjUuulp6cXSbj4q1+/fpTjBRdcgKzt2rWrTt0o26AhOHKB/ON0AhWA402pQcULyfDiW5rRzTQiTMqTxIIK/E22fEPUXJbNQyfoD8okksMWHi0J2PTp0wcJmTRpkm1vJE9TUlLQ2WceoUONfOfMQelQjUCeDRo0CJFr0KABRcwdTSxYJ598MhNJWeTLRUHvvPNOrmwL0A0UPL8O2ZCWlsZWpx1FtjZ0YIVcCTodctUZLtG88MILxgmX7SSayS2EUrZs2d1ytyQsr7jiCh5eZDy1vxeR6AXfRvwHq7QLEpJN3kjCpZdeWqZMmb2ydqNVq1bVq1enA/qAKKFUDB8+HKJDWo466qhq1ar17t2b+3eYrjj6T3shHTt2VKp9+OGH6sA26+AF2Hb++ecrHTmEpNIOyM4rRo82CrrBc9y4cdnS49Fsgp+oOt54442GDRvCBoV29uzZp5xySrgEA5kxqIbsWb58OURWv359jmvw6BfKiKPYIZlfo3vqMM6TKv/UNxua2l/lKAAoIeowurcHfphttGdj/ExZ6m7koCTjtJxYgikm44RO84wZM5YuXWoKwTPjoRp+gT4bM2aM6kXGnOP49l4mIyowzzkagvo7IyMDXh133HGgWqZsz1ZZxQdDufvuu/FXpUqVMmVXOncu2WZjtWT4BA+++eYbxiEgJxdR4wKcm1bd7wU+PfTQQ0wRQqGQkUEILjU1tVy5ctCX0BdQnHqFuqtYFhJuEaBgNW/enAkYPHhwvoxqqjaGKPv378/+morv1FNPpWM8+/btS0vj6HBkWMzMRhCooxmQ3fN1FXpWr9AoyHWKEgXAOCdtIQ7ato1YdTrUfljaN1xoXxD1FTbVIFnEZ9asWYxbSJrGyAPYUzO5eEOVb4TxuwVMQr169XjneFhu5da8KSjLjchEW8agqd3ps80sk2xCQLYbNmygPXRnrlyNDfNJJ53EEBkHwhU0/YQlS5RL8lz00LNnT+NsHlMaFA9uqiFgqIrk5GSWXdRx3DNjJF87dOhgnL2sLD1BWRREB9zmgLqjXbt2MCxbtgxuoPPtjgUBfcYVCka8JRAczyTTVRscBLfdhOTMotq1a/NCZz2KLFsOo+SrkWzOk15t06ZNyRi7x+CFTTXwkl5xBQojnyOjDBEZ8Qk4003t27cH73OlI2WXcmQ5Gjd5sg2RNjTEbIYWBP3XHv2BOV/AV3IOqoGFv3Xr1mgoB2RDGjIFlshKvLJ1mydQr4ixY8fCARqpxhIRDVOmTEFzjdKbM2cOJycV+y29XripVhhEnCUx3qj7iPjbWApAcahmRNmyae/+cMgDWrDw43mHFIpMNfZTaI5fKx2C0OaOzzYvikM1rad9gbqgrbEiNcsOEcSgGhubduWIJrMtO7aU0StZvHixWhppKtptFPWBHrJZbaJ1YY4z/cxRtJiNTU4nsH+gfupftGTfMCIzgznWRR/qyX6hxcZOeNC6IqOg1oKdTG28hhJyRYY9ZwgzJ2DYJSeoZe1fXNh7oK7I0O4eetroDCLSJ598MhcQB+UEIQ5Vh2RQDV1U7SXZK0WbNGnSqVOnXbt2rVy5MikpacaMGcYzhYIfzzrrLJorVarECzeMJMO1DocIOIhEn3+hh2J8//33VapUCcgB2PxUJJ4xevGvyFAPGYGwjHqgc8fXiDUPqy6Df/IVGfrjrFmz0G1/9913+arrOqtWrZol5+iwwHhlciCvyCAQOWQ5+sD0unfv3rRHubnuuutoZsbTXKtWLcqUSzc5ToE+P6gzdOhQWygqemSMPQhHlu8VqCURib5tg1mrpYJu8mVKNOAsds13Lvr4w5eig5rStkHc7rrrLuQfX6+55pocZ9VNRMbZsxN7RQYNAA8pQ/RyZAavcuXKITnPtnbt2q+//jrdUN/rLyb6UGnbfm9irshgAkBhUAG6LV/mnaCcdGysRo0aNDCbEXuuQfjkk08QdfxCT1j1/Cqnz2nk7MxAAuAVPkGr6Tr6gpIRdm7bMDImqXmmVAvLjJCt8OyLPvYLepi/vysyIG5wiKEgFaNGjUICkXA607xP2BUZ8JYFHl+VRjt27EAojBVU3emnn54n0/DeMsyyFDhQV2Qg3tOmTaP5tNNOI9+5r4lSaNWqFZPNRMJBzZo1A3LKkro0IjXO1G7ZsoVxVRVIfY70N2zYkDYENRObAsbKY/JAb9vgZBS/qhojbJHxog9XOY4DdcnYeq/IMBIclE3ZsmVh+F3OC6KlUkTTaBJyRYbKirozRxq+jRs31uwIyHUZ9913nxXIH8g/gFdkEBMmTGAhgDTRCECThVP6iBa0N6dBkCodPuZ5kSiIIbkqBfU6936iVjXOFhiWeGZnSKauJ0+evG3bNuOQhjxjydPyR1Hutm7bANAiSU1N/cc//mFkJ6ntPiDTBvnWRR861REfVDmUe7iAKzIIbhTgV06SQlx5To+HPiTsigyNWEDOEevQoQMkxlM1OXPD6zKgnu0k2DiQV2TsdVrBdkeGKppmlvIsmX3zNg81EpkyaWgkn1x1h5ZFhTYaiIic1GxkblSznBqUtZtrnT4ayypKikkv+tDC5w3UC3rCX+iPqzVjC4Gh01lQmv/8MT+BV2SofVjWyjN63NpppGCz4DHEmGw78FdkaPIYjGaqUl5h11CUtb3UMeLcZaE2REj2dxRUu+XI6bg0R2QXAkVGG81vwp6q1zNdCWggBlFQQApbh7GMRWJdkUGFBN9ijunYqpFgnNWG0VBvYyJclCsyVA3bJdw4BZ4R229Np2lR9rCpbZwGKAWuOkjdqLmQiE21sIBmm1tB2Z2xR7aI2Y0YV5Mz3zpG34hvGrOQzGpTFir0TM+lbjb2CEwsfWCT2PaB8t0vw2yo5/THlWrj5KudczarwtIv0dfSwm/7uyLDleU2j7VeYltI7V0IxrrSIPhnX5FhnGKxR/Zj0oaFhq+IPSPNp2vxjzfGLniVnJ1bZn8lniCJGZwdYp4zAhz0DFLsF5mFuCKDYVGxhWVrhXFKjilczIsKJodNdTVnW1dk2Hmk7vNl1zSr/lxZMUqXXn7EJ03On31FhlZ/TI/dhtWCTh3WpUsXtNDt6kzrrzzZHg1nWrD2KUkrcjSrDcsKaedVXUSWDEUah+W23lJ/NL9DBVz0EQdabHYVfEVGUKBmhrtXQMtSh50LNDMCtujC0lDjK6VEG2aNlsaCCoOrQaKwKyJjidrOxyLBTbV9VoFAo0aNOOyOrke9evWCsmQPnfxzzz2XbrRDzteJEyfmy7JgIxvZ2T388MMP4eCDDz4gLTSKOdJpv/DCC/OlBc2pAvYlkc0xVSPDYnAc7CC47i8i63bQvYeDqlWrkpF2DV5I7PeKDJYcnZDgajBde1iYrmXhESjEFRlZ0TuiVcKNGzc+55xzgjLBY0Q+rKy81eiBvCKD+QT9BH8HDhyIICHfnj17qn7SK7ADspiR7tGpzpfxz6uuuirk7CL817/+ZazZHgJfqQPgvw6xsmKl2VX4mDzmItcA6pYZiJ4D99pIQt7z96B10Qczw1UtusAIqEJlQXf1oGm+44479NCX3r172zltN5wTc0WGAoyZMGEC43n55ZdriBxkyXOu1nQheACvyICw2AThoVcsE8bZpETQEhLUHSsoZ8inFStWZMkWJlqGZLmscU5dMLF0L8+xCshYpYovX+bsmdk27fS2DShX7SAHnAXf+kqDXvTBHNqvhrOppuRwXZHB5GzdupVTRpDV+PHjQSm0IphD9CqUwCsyRNHvc3b22WeTBzudu84JPWPGy04j4s06UFdksP34zDPP8FXnoCApLRbcNhNyrq3AL23atAnIQWKId5MmTbKdnbFr165FdHk5kLFSS3LgtUGDBrQxjmZKS0sD18kPplzTT1EiJ3hvixFSUkaUPgJChNlN2+tc9MFDX/4XRsGwqWYkMjGvyEAtj+oGEkfZ+F2WUSClWp+Sbayk9iTkigwVTkBmFCABJBY1nXHqAagDu+vgVe2sgl1VCrPvzD/1igyGNGrUKMh63bp1KJovv/zyW2+9hbYLu76TJ08GG4xkBtpGjCLqKaRw1apVUGCfffbZggULOM9dvXp1ONbpP0WOjEuhKcB7VYignIpKlb7b2WDHbM6Nvm0DTUColosvvhguNZspRCg8ePKTddEHrwvaL2yq/V7wFRlkLXMan1BtQUpo4ak/RCKvyIBLNFqoaVq0aAFZffLJJwj6/fffN3LDCdp5UE507KLa7/4VGX9pRPy9BQXAp1ppgjrMlKCW+RvDp1rpozB15SEIn2qliaB/RUbB8KlW+tBhLR82fKr5SBB8qvlIEHyq+UgQfKr5SBCiqKaTX0ZGhnz4KCRyZAdN/Dn4GFotIyPDtXLah4/42L59uw5fFwQ31fLkAMT9/ubDh41M5xCJOAM9bqr58FESxFmQ51PtAMM+6SOOSkA9w2UvRrIzV05SdjsqNEgILiQJWqeiKhgTW1GVfP7Dp9qBBxfkKM90p0LM3I1YuwaLDXtZQMhZNe1CyNpwZJuLDZ9qBx75AqiWbNkcxT6dfqUGIr127dqln4q3Tslbwdnb3hS6WNJlLgl8qh14DB06tEKFCvfff/9bb73VoUOHPn368AicN998c8iQIcccc8y9996LGnPt2rW6yL5Zs2auIwEKiWHDhgUCAS7rv+WWW3r16oXXbt26uZwlJSV17doVEXOZSwKfagcY1GG6nJhLfBcuXHjzzTezCdWwYUPWd8cffzyXyEPNgGp/eFEUoJru3r37tm3b4Em/fv3uu+8+hMitScbRne++++7UqVNHjx6NT7Y5yqOio6T/+yghbKqhlcbTdFasWMHdK1BmjRs3pktk9nvvvYeMh0469dRT7YbU//wqBPDX1VdfnZ6ejkDHjh3bs2dPaNC77rqLGz7o55gxY8aNGzdjxoyjjz7aNrv9KiJ8qh1geLUaqk7Um2BVWK5pO+GEE2C/YcMGkO/TTz+lduHxneAcuxRFWul//fXXb9myJSwnq6HBd8UVV4BtJFmenG+amZnJi3JSUlJss9ujIsKn2gGGTbWIbOGB/rj22muNs7Wsbt26Rg7xg87jRiwQq0yZMnp+WyT6/JT4wL+9e/emVktNTS1fvjwaamvWrMGnb7/99sILL+R+ouHDh9eqVStfjl5Us9uvIsKnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBMGnmo8EwaeajwTBp5qPBOH/ARvTmQ+jBddtAAAAAElFTkSuQmCC>