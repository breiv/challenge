# Breiv mobile challenge

Develop an app that consumes Moip API. The app should login and retrieve the authentication and list all orders from the account logged; clicking in one of the orders should open its details. You may follow the given mockups as guidelines for your challenge.

##### Login screen
In order to retrieve the authorization data you must do a `POST` operation at https://connect-sandbox.moip.com.br/oauth/token with the following data as `form-urlencoded`.

`REQUEST`
```json
  "client_id": "APP-H1DR0RPHV7SP",
  "client_secret": "05acb6e128bc48b2999582cd9a2b9787",
  "grant_type": "password",
  "username": "#{APP USER MOIP LOGIN}",
  "password": "#{APP USER MOIP PASSWORD}",
  "device_id": "um id para o device",
  "scope": " APP_ADMIN"
```
The response will data needed to access the others requests. 
`RESPONSE`
```json
{
    "accessToken" : "ACCESS_TOKEN",
    "moipAccount" : "MOIP_ACCOUNT",
    "id" : "ID"
} 
```

<img src="https://github.com/breiv/challenge/blob/master/mobile/login.jpg" width="360">

In order to authorize all other requests, you will have to add the following authorization to the Header:
`"Authorization", "OAuth ACCESS_TOKEN"`

You can use this moip account to login on your app: `user: moip-test-developer@moip.com.br` `pass:  testemoip123`

##### List orders screen
Make a`GET` operation at url https://sandbox.moip.com.br/v2/orders with the given authorization at the Header. You can see the JSON response as well its description and other details at the link above. 
https://dev.moip.com.br/reference#listar-todos-os-pedidos 

You must show at least the following data:
* Total amount
* Email
* Own id
* Current Status
* Current status date


<img src="https://github.com/breiv/challenge/blob/master/mobile/order%20list.jpg" width="360">

##### Order detail screen
Make a `GET` call at url https://sandbox.moip.com.br/v2/orders/ORDER_ID with the given authorization at the Header. You can see the JSON response as well its description and other details at the link above. 
https://dev.moip.com.br/reference#consultar-pedido

You must show at least the following data:
* Total amount
* Emai
* Own id
* Id
* Operation type
* Buyer name
* Buyer email
* Creation date
* Current status
* Current status date
* Total amount
* Tax
* Liquid value
* Number of payments

<img src="https://github.com/breiv/challenge/blob/master/mobile/order%20detail.jpg" width="360">

#### About the challenge
* You need to follow the same design as showed on the screenshots.
* It must be written in kotlin or swift.
* You should store the login data. If you reopen the app, it shouldn't ask for the login again, it must go direct to the order list screen.
* When you click in one of the orders at the list order screen, you must show another screen with de order details.
* Unit tests are required

#### Pluses
* Pagination with endless scroll at the order list screen.
* UI tests
