![Grupo Banklot](./images/logo-banklot.png)

## Tabla de Contenidos
- [Documentación de la API de la Lotería](#documentación-de-la-api-de-la-lotería)
  - [Tabla de Contenidos](#tabla-de-contenidos)
  - [Endpoints](#--endpoints)
  - [Verbos](#verbos)
  - [Códigos de Estado](#códigos-de-estado)
  - [Autenticación](#autenticación)
    - [Inicio de sesión](#inicio-de-sesión)
    - [Cerrar sesión](#cerrar-sesión)
  - [Consultas](#consultas)
    - [Vista del Boleto](#vista-del-boleto)
    - [Ver Boleto Impreso](#ver-boleto-impreso)
    - [Ver Último Boleto](#ver-último-boleto)
    - [Cancelar Vista del Boleto](#cancelar-vista-del-boleto)
    - [Vista del Boleto Ganador](#vista-del-boleto-ganador)
    - [Boletos Vendidos](#boletos-vendidos)
    - [Obtener Datos](#obtener-datos)
  - [Acciones](#acciones)
    - [Pagar Boletos](#pagar-boletos)
    - [Copiar Boletos](#copiar-boletos)
    - [Cancelar un Boleto](#cancelar-un-boleto)
    - [Revertir un Boleto](#revertir-un-boleto)
    - [Crear un Boleto](#crear-un-boleto)
  - [Informes](#informes)
    - [Informe por Periodo](#informe-por-periodo)
    - [Informe de Resultados](#informe-de-resultados)
  - [Quiosco](#quiosco)
    - [Jugadas Válidas](#jugadas-válidas)
    - [Hora](#hora)
    - [Sorteo](#sorteo)
    - [Productos](#productos)

Bienvenido al portal para desarrolladores de Grupo Banklot. Aquí encontrarás una referencia sobre cómo integrar **Grupo Banklot** en tus aplicaciones y flujos de trabajo existentes utilizando nuestra API [RESTful](https://es.wikipedia.org/wiki/Transferencia_de_Estado_Representacional) basada en [HTTPS](https://es.wikipedia.org/wiki/HTTPS). Nuestra API usa verbos [HTTP estándar](https://es.wikipedia.org/wiki/Protocolo_de_Transferencia_de_Hipertexto#Métodos_de_solicitud) para especificar la intención de la operación, y códigos de [estado HTTP](https://es.wikipedia.org/wiki/Lista_de_códigos_de_estado_HTTP) para indicar la respuesta a esas operaciones. Se emiten tokens de seguridad al iniciar sesión, que se incluyen como [cabeceras HTTP](https://es.wikipedia.org/wiki/Lista_de_campos_de_cabecera_HTTP).

Usa el selector de idioma en la parte superior para mostrar ejemplos en tu idioma de preferencia, y usa el selector de versión dentro de la muestra de código para ver un ejemplo de solicitud/respuesta para esa versión en particular.

# EndPoints
Las llamadas a la API del portal de ****Grupo Banklot**** usan la siguiente URL base:
[https://staging.loterias24.com/](https://staging.loterias24.com/)
Las llamadas a la API listadas a continuación proporcionarán la URL que debe ser añadida a este endpoint al hacer solicitudes.

## Verbos
Se usan los siguientes verbos HTTP. Se muestra una descripción de cómo se usa cada uno. Por favor, consulta cada API individualmente para la sintaxis adecuada para la creación o actualización de recursos, ya que pueden usar uno de PUT, POST o PATCH.
- GET - recuperar un recurso
- PUT - actualizar un recurso
- PATCH - actualizar un recurso
- POST - crear un recurso
- DELETE - eliminar un recurso


# Estado de Códigos
Los códigos de estado devueltos por la API incluyen los siguientes:
- 200 - OK - la solicitud fue exitosa
- 201 - Created - el recurso fue creado
- 204 - No Content - la solicitud fue exitosa, pero no hay datos para devolver
- 301 - Moved Permanently - el recurso se puede acceder a través de otra URL
- 400 - Bad Request - hay un problema con la solicitud que enviaste
- 403 - Forbidden - fallo de autenticación o versión de API obsoleta
- 404 - Not Found - recurso no encontrado
- 500 - Internal Server Error - hay un error de nuestro lado, ¡envíanos un correo electrónico!

# Autenticación

## **Inicio de sesión**
La autenticación implica el uso de una única API. Sin embargo, se deben usar múltiples APIs de autenticación y administración sucesivamente para recuperar los metadatos apropiados para usar en la consulta de la API.

1. Para iniciar sesión con credenciales, llama a POST /auth/login. El cuerpo de la solicitud debe incluir los siguientes pares clave-valor.

```
Endpoint: /auth/login
Method: POST
Headers:
```

- Tipo de Contenido: ****application/json****

- **Request Body:**


```json
{
    "email": "username@banklot.net",
    "password": "******"
}
```
- Respuesta:

- Recupera un token y lo establece en la variable de entorno para futuras solicitudes.

- Script de Evento:

- Analiza el cuerpo de la respuesta y establece el token en el entorno.

**IMPORTANTE ** *Tras una respuesta exitosa, extrae el valor *`x_auth_token`* del JSON de la respuesta. Este valor es el token de seguridad que debe ser incluido en las llamadas subsiguientes a la API usando el *`x-auth-token header`*.*

# **Cerrar sesión**
Para cerrar la sesión existente, llama a `GET /auth/logout` con el `x-auth-token` configurado.

## Consultas
## **Vista del Boleto**

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
## **Ver Boleto Impreso**

```
Endpoint: /user/ticket/image/f3f30cdb-2165-487b-bfd0-c990b7ab62c1 
Method: GET 
Headers:
```
- Tipo de Contenido: ****application/json**** 

Solicitud: **El boleto debe tener el formato uuid** como parte de la URL, no del cuerpo.

**Respuesta:**

```

```
## ## 
## **Ver Último Boleto**

```
Endpoint: /user/ticket/last 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la Solicitud: No se requiere cuerpo.

**Respuesta**:

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
## **Vista de Boletos Anulados**

```
Endpoint: /user/ticket/ 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la Solicitud: Debe contener el rango de fecha y hora con el estado.

Solicitud: Debe especificar el rango de fecha y hora.


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

**Respuesta**:

```json
{
    "status": 200,
    "response": [
        {
            "id": "639a1521-49b9-4876-a36c-36c621593930",
            "ticket_number": 13239361,
            "created_at": 1721660369,
            "user_id": 864,
            "email": "username@banklot.net",
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

## **Vista del Boleto Ganador**

```
Endpoint: /user/ticket/ 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json****

- Cuerpo de la Solicitud: Debe contener el rango de fecha y hora con el estado


**Solicitud:**

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

**Respuesta:**

```json
    "status": 200,
    "response": [
        {
            "id": "af681029-87a2-4834-b7f9-56d88ee3a74e",
            "ticket_number": 23315522,
            "created_at": 1728066656,
            "user_id": 864,
            "email": "username@banklot.net",
            "status": "winner",
            "total": 33,
            "prize": 330,
            "entity_id": 213,
            "parent_id": 212,
            "entity_name": "test-1",
            "parent_name": "test"
        },

```

## Boletos Vendidos

```
Endpoint: /user/ticket/ 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json****

- Cuerpo de la Solicitud: Debe contener el rango de fecha y hora con el tipo de transacción


**Solicitud:**

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
**Respuesta:**

```json
{
    "status": 200,
    "response": [
        {
            "id": "16baefc2-5c3e-4f17-a26c-c19808e22655",
            "ticket_number": 30213646,
            "created_at": 1724896556,
            "user_id": 864,
            "email": "username@banklot.net",
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

## Obtener Datos

```
Endpoint: /gaming/get-data 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- **Solicitud:**

**Respuesta:**

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

# Acciones

## Pagar Boletos

```
Endpoint: /user/ticket/pay 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la Solicitud: Debe contener el número del boleto, pin_number y la fecha.

**Solicitud:**


```json
{
  "ticket_number": 10653459,
  "pin_number": 84038675,
  "date": "2024-09-16"  
}
```
**Respuesta:**

```json
{
    "status": 200,
    "error": "not a winner"
}
```

## Copiar Boletos

```
Endpoint: /user/ticket/copy 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la Solicitud: Debe contener el número del boleto y la fecha.

**Solicitud:**

```json
{
  "ticket_number": 71998218,
  "date": "2024-09-17"  
}
```
**Respuesta:**

```json
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
## Anular Boletos

```
Endpoint:: /user/ticket/cancel 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Debe contener el número de ticket.

**Solicitud:**

```json
{
  "ticket_number": 18712010
}
```
**Respuesta:**

```json
{
    "status": 400,
    "error": "no rows in result set"
}
```

## Revertir Boleto

```
Endpoint: /user/ticket/revert 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Debe contener el número de ticket.

**Solicitud:**

```json
{
  "ticket_number": 71998218
}
```
**Respuesta:**

```json
{
    "status": 401,
    "error": "ticket already rejected by user"
}
```
## **Crear un Boleto**
```
Endpoint: /user/ticket/create 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Debe contener el monto, even_id, game_id y el wager.

**Solicitud:**

```json
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
**Respuesta:**

```json
{
    "status": 409,
    "error": "events are not open. closed events: [18859]"
}
```

# Informes

## Reporte por Periodo
```
Endpoint: /gaming/reports 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Must contain the date time range, group and category.

**Solicitud:**

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

**Respuesta:**

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

## Resultados de Reporte 
```
Endpoint: /gaming/result/0 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json****

- Cuerpo de la solicitud: Debe contener el rango de fechas.

**Solicitud:**

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

**Respuesta:**

```json
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
# Kiosko
## Jugadas Válidas

```
Endpoint: /gaming/inventory/template
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: El cuerpo no es requerido. 

**Respuesta:**

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
```

## Hora
```
Endpoint: /gaming/time 
Method: GET 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Debe contener el rango de fechas.

**Solicitud:**

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

**Respuesta:**

```

```
## **Sorteo**
```
Endpoint:/gaming/events/search/kiosk 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: Debe contener el rango de fechas, game_category y status.

**Solicitud:**

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

**Respuesta:**

```json
{
    "status": 201,
    "total": 0
}
```

## Productos

```
Endpoint:/gaming/products/search 
Method: POST 
Headers:
```
- Tipo de Contenido: ****application/json**** 

- Cuerpo de la solicitud: El cuerpo no es requerido. 

**Respuesta:**

```json
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
