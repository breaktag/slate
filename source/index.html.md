---
title: TabHub Public API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  # - ruby
  # - python
  # - javascript
  - php

toc_footers:
  - <a href='#'>Request an OAuth Client</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the TabHub Public API
---

# Introduction

## Version History

Version | Description | Date
-------------- | -------------- | --------------
1.0 | Initial Release | 2023-02-15

## Overview 

The TabHub Public API is built around RESTful practices and designed to receive data via HTTPS requests. The following sections describe each action that is available and the information the system expects to receive in the request and the information that is returned in the response.

Access to the TabHub API is secured via OAuth2. Each third party will have an access token that needs to be passed in conjunction with each subsequent request.

The OAuth2 password grant allows you to obtain an access token by using an email address and password of an existing TabHub user. You will gain a short lived access token and a longer life refresh token, which is used to update your short lived tokens and keep you connected.

This document will also provide examples of each request and response in a JSON format.

Responses from the TabHub API will include a suitable HTTP header such as 200, 404 or 401 for the header portion of the response. 

You should never expose your Access Token, Refresh token, username or password to anyone or in any client-side web application.

# Authentication

## Obtaining an Access Token & Refresh Token

> Obtaining an Access Token & Refresh Token

```php
$http = new GuzzleHttp\Client;

$response = $http->post('https://mysite.rposcloud.com/oauth/token', [
   'form_params' => [
      'grant_type' => 'password',
      'client_id' => 'your-client-id',
      'client_secret' => 'your-client-secret',
      'username' => 'your-tabhub-email-address',
      'password' => 'your-tabhub-password',
      'scope' => '*'
    ],
]);

return json_decode((string) $response->getBody(), true);
```

> The above command returns JSON structured like this:

```json
{
   token_type: "Bearer",
   expires_in: 1296000,
   access_token: "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImF....",
   refresh_token: "def50200b0fb5bd8ed0c08cef8951d7664d4605ac747...."
}
```

To obtain an access and refresh token paid you must make the following Authorisation request via POST. You must supply a valid TabHub Email Address and Password combination which you will have received when you signed up to BarTab. You will also need a client_id and client_secret which will be granted to you by Tabology on request. In this example, we’ll use the Guzzle HTTP library to gain the tokens:

## Refreshing Tokens

> Refreshing Tokens

```php
$http = new GuzzleHttp\Client;

$response = $http->post('http://mysite.rposcloud.com/oauth/token', [
    'form_params' => [
        'grant_type' => 'refresh_token',
        'refresh_token' => 'the-refresh-token',
        'client_id' => 'client-id',
        'client_secret' => 'client-secret'
    ],
]);

return json_decode((string) $response->getBody(), true);
```

Typically access tokens are only short lived for up to 15 days. Refresh tokens will expire after 30 days.
If your access token expires, you will need to use the refresh token to generate a new one. The refresh token was provided when the original token was issued. In this example, we'll use the Guzzle HTTP library to refresh the access token:

# API Resources

## Base Requests

The Base URL for all TabHub API requests is `https://mysite.rposcloud.com/` where `mysite` is the site you have connected to.

## Request Headers

> Request headers example

```php
$client = new GuzzleHttp\Client;

$response = $client->request('GET', '/api/member', [
    'headers' => [
        'Accept' => 'application/json',
        'Authorization' => 'Bearer ' . $accessToken,
    ],
]);
```

When calling any API route, your application's API consumers should specify their **Access Token as a Bearer token** in the `Authorization` header of the request. You must also set the `Accept` header to use `application/json` For example, when using the Guzzle HTTP library:

## Search Params

To use the search params available for each request, append the `key`, `value` pairs as a query string to the Request URI

e.g: `https://mysite.rposcloud.com/api/bookings?from=2022-01-01&to=2022-01-31`

# Bookings

## The Booking Object

### Attributes

> The Booking Object

```json
{
  "id": "bf3a4974-f0e9-11e9-86c3-080027d0dffe",
  "name": "John Doe",
  "phone": "+441234567890",
  "email": "john@example.com",
  "date": "2019-12-24 13:30",
  "duration": 360,
  "tables": [],
  "covers": 6,
  "deposit_tab": 7,
  "tab":null,
  "tab_status": null,
  "created_by": "John Manager",
  "created_on": "2019-10-20",
  "updated_by": "John Manager",
  "updated_on": "2019-10-20",
  "notes": "allergic to shellfish",
  "confirmed": "Y",
  "member": null,
  "deposit_amount": 100,
  "deposit_spent": 9.99,
  "deposit_remaining": 90.01,
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the booking
`name` | ***string*** The name associated with the booking
`phone` | ***string*** The telephone number associated with the booking
`email` | ***string*** The email address associated with the booking
`date` | ***string*** The date and time of the booking (Format `YYYY-MM-DD HH:mm`)
`duration` | ***int*** The duration of the booking (in minutes)
`covers` | ***int*** The number of covers for the booking
`tables` | ***object*** See Tables object reference
`created_by` | ***string*** The user who created the booking
`created_on` | ***date*** The date at which the booking was created
`notes` | ***string*** Any optional notes attached to the booking, such as special requests or allergy notices
`confirmed` | ***string*** The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled

### Extra Attributes (not available on All Bookings call)

Key | Description 
-------------- | --------------
`deposit_tab` | ***int*** The ID of the Deposit Tab <br> ***note:*** *This is not available on the All Bookings endpoint*
`tab` | ***int*** The ID of the Tab (after marking as arrived) <br> ***note:*** *This is not available on the All Bookings endpoint*
`tab_status` | ***int*** The status of the Tab (after marking as arrived) <br> `OPEN` - Tab is open/active  <br> `Closed` -Tab is closed <br> `SETTLED` - Tab is settled at £0 <br> ***note:*** *This is not available on the All Bookings endpoint*
`deposit_amount` | ***float*** The total amount of deposit for the booking <br> ***note:*** *This is not available on the All Bookings endpoint*
`deposit_spent` | ***float*** The total amount of deposit spent on the booking tab <br> ***note:*** *This is not available on the All Bookings endpoint*
`deposit_remaining` | ***float*** The total amount of deposit remaining on the booking tab <br> ***note:*** *This is not available on the All Bookings endpoint*
`member` | ***string*** The ID of the member if linked to the booking <br> ***note:*** *This is not available on the All Bookings endpoint*

## All Bookings

```json
{
    "success": true,
    "data": [{
        "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
        "name": "Ben Riley",
        "phone": "+441234567890",
        "email": "team@tabology.com",
        "date": "2019-10-17 15:23",
        "duration": 240,
        "covers": 3,
        "tables": [{
            "id": 1,
            "name": "Table 01",
            "max_covers": 4,
            "activity": null,
            "area": null,
            "show_to_customer": "Y",
            "type": "rbar",
            "tab":null,
            "status": "FREE",
            "meta": null
        },{
            "id": 2,
            "name": "Outside Bar 1",
            "max_covers": 6,
            "activity": null,
            "area": null,
            "show_to_customer": "Y",
            "type": "rbar",
            "tab":null,
            "status": "FREE",
            "meta": null
        }],
        "created_by": "API",
        "created_on": "2019-10-31",
        "notes": "",
        "confirmed": "Y"
    },{
        "id": "bf3a4974-f0e9-11e9-86c3-080027d0dffe",
        "name": "Ian Berry",
        "phone": "+441234567890",
        "email": "team@tabology.com",
        "date": "2019-12-24 13:30",
        "duration": 360,
        "tables": [],
        "covers": 6,
        "created_by": "John Manager",
        "created_on": "2019-10-20",
        "notes": "allergic to shellfish",
        "confirmed": "Y"
    }]
}
```

This endpoint retrieves all bookings

`GET https://mysite.rposcloud.com/api/bookings`

### Search Params

Key | Example 
-------------- | --------------
`on` | `2022-01-01` <br>Show bookings on this date
`from` | `2022-01-01` <br>Show bookings on this date and the future
`to` | `2022-01-01` <br>Show bookings before this date and the past

## Single Booking

> Single Booking Response

```json
{
    "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
    "name": "John doe",
    "email": "john@example.com",
    "phone": "07891234567",
    "date": "2019-10-17 15:23",
    "duration": 240,
    "covers": 3,
    "tables": [...],    
    "deposit_tab": 6,
    "tab": null,
    "tab_status": null,
    "created_by": "John Manager",
    "created_on": "2019-10-17 15:23:53",
    "notes": "Allergic to eggs",
    "confirmed": "Y",
    "updated_by": "Jane FOH",
    "updated_on": "2019-10-17 15:23:53",
    "deposit_amount": 20,
    "deposit_spent": 5,
    "deposit_remaining": 15,
    "member": null,
    "deposit_payments": [...],
    "deposit_saved_balances": [...],
    "deposit_links": [...]
}
```

Fetches the full data for a single booking

`GET https://mysite.rposcloud.com/api/bookings/{booking_id}`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

## Create a Booking

> Create Booking Response

```json
{
    "success": true,
    "message": "Booking successfully created",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2019-10-17 15:23",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 6,
      "tab": null,
      "tab_status": null,
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "Y",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 20,
      "deposit_spent": 5,
      "deposit_remaining": 15,
      "member": null,
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Creates a new booking

`POST https://mysite.rposcloud.com/api/bookings`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name associated with the booking
`email` | ***<span style="color:#dd4b39">required</span>*** ***string*** `john@example.com`<br>The email address associated with the booking
`date` | ***<span style="color:#dd4b39">required</span>*** ***string*** `2022-01-01 17:15`<br>The date and time of the booking (Format `YYYY-MM-DD HH:mm`)
`phone` | ***string*** `+441234567890`<br>The telephone number associated with the booking
`duration` | ***int*** `120`<br>The duration of the booking (in minutes)
`covers` | ***int*** `6`<br>The number of covers for the booking
`tables` | ***object*** `[]`<br>See Tables object reference
`notes` | ***string*** `Can we have a baby high chair`<br>Any optional notes attached to the booking, such as special requests or allergy notices
`deposit_amount` | ***float*** `150.00`<br> Adds an initial deposit to the booking
`deposit_type` | ***string*** `Cash`<br> Must be a valid credit line type
`confirmed` | ***string*** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> ***note:*** *This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created* 


## Update a Booking

> Update Booking Response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2023-02-20 17:30",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 6,
      "tab": null,
      "tab_status": null,
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "Y",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 20,
      "deposit_spent": 5,
      "deposit_remaining": 15,
      "member": null,
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Updates an existing booking

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name associated with the booking
`email` | ***<span style="color:#dd4b39">required</span>*** ***string*** `john@example.com`<br>The email address associated with the booking
`date` | ***<span style="color:#dd4b39">required</span>*** ***string*** `2022-01-01 17:15`<br>The date and time of the booking (Format `YYYY-MM-DD HH:mm`)
`phone` | ***string*** `+441234567890`<br>The telephone number associated with the booking
`duration` | ***int*** `120`<br>The duration of the booking (in minutes)
`covers` | ***int*** `6`<br>The number of covers for the booking
`tables` | ***object*** `[]`<br>See Tables object reference
`notes` | ***string*** `Can we have a baby high chair`<br>Any optional notes attached to the booking, such as special requests or allergy notices
`confirmed` | ***string*** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> ***note:*** *This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created* 


## Mark a booking as arrived

> Mark booking as arrived Response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2023-02-20 17:30",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 6,
      "tab": 7,
      "tab_status": "OPEN",
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "Y",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 20,
      "deposit_spent": 5,
      "deposit_remaining": 15,
      "member": null,
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Marks a booking as arrived.

This will take an existing booking and its deposit and transfer the deposit amount across to a new open tab at the venue.

*Note*: `tab` column will be populated. `tab_status` will be `OPEN`. Tab will appear on the EPOS pre loaded with the deposit, and can now have items added to it usiong the add-item API call.

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/arrival`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

<aside class="notice">
Only bookings that do not have a linked <code>tab</code> can be marked as arrived
</aside>

## Mark a booking as departed

> Mark booking as departed Response

```json
{
    "success": true,
    "message": "Booking for John Doe [bf3a4974-f0e9-11e9-86c3-080027d0eccd] was marked as departed",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2023-02-20 17:30",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 6,
      "tab": 7,
      "tab_status": "SETTLED",
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "Y",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 20,
      "deposit_spent": 5,
      "deposit_remaining": 15,
      "member": null,
      "tab_data": [...],
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Marks a booking as departed at the end of the customers session.

This will perform a check that the tab associated with a booking is settled and will return either the details of the settled Tab, or an error message explaining that the Tab needs settling

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/departure`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

<aside class="notice">
Only bookings that have a linked <code>tab</code> marked as <code>SETTLED</code> can be marked as departed
</aside>

<!-- ## Mark a booking as cancelled

> Mark booking as cancelled Response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2023-02-20 17:30",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 6,
      "tab": null,
      "tab_status": null,
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "C",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 20,
      "deposit_spent": 5,
      "deposit_remaining": 15,
      "member": null,
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Cancels a booking and sends an email to the customer

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/cancel`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

## Mark a booking as declined

> Mark booking as declined Response

```json
#
```

Declines a booking request and sends an email to the customer

<aside class="notice">
Only booking requests (<code>"confirmed": "R"</code>) can be declined
</aside>

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/decline`

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name associated with the booking
`email` | ***<span style="color:#dd4b39">required</span>*** ***string*** `john@example.com`<br>The email address associated with the booking
`date` | ***<span style="color:#dd4b39">required</span>*** ***string*** `2022-01-01 17:15`<br>The date and time of the booking (Format `YYYY-MM-DD HH:mm`)

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking -->

## Add a deposit to an existing booking

> Add a deposit to an existing booking Response

```json
{
    "success": true,
    "message": "Successfully added deposit of £25.00 to John doe [bf3a4974-f0e9-11e9-86c3-080027d0eccd]",
    "data": {
      "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
      "name": "John doe",
      "email": "john@example.com",
      "phone": "07891234567",
      "date": "2023-02-20 17:30",
      "duration": 240,
      "covers": 3,
      "tables": [...],    
      "deposit_tab": 7,
      "tab": null,
      "tab_status": null,
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "confirmed": "Y",
      "updated_by": "Jane FOH",
      "updated_on": "2019-10-17 15:23:53",
      "deposit_amount": 45,
      "deposit_spent": 5,
      "deposit_remaining": 40,
      "member": null,
      "deposit_payments": [...],
      "deposit_saved_balances": [...],
      "deposit_links": [...]
    }
}
```

Adds a deposit line to an existing booking

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/add-deposit`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking


Key | Example 
-------------- | --------------
`deposit_amount` | ***<span style="color:#dd4b39">required</span>*** ***string*** `25`<br>The amount in (£/$/€) of the deposit to be added
`deposit_type` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Cash`<br> Must be a valid credit line type

<aside class="notice">
Only bookings that have not been yet been marked as arrived can have a deposit added to them
</aside>

# Tables

## The Table Object

### Attributes

> The Table Object

```json
{
    "id": 1,
    "name": "Table 01",
    "max_covers": 4,
    "activity": null,
    "area": null,
    "sort": 0,
    "show_to_customer": "Y",
    "type": "rbar",
    "tab": null,
    "status": "",
    "meta": null
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the table
`name` | ***string*** The name associated of the table
`max_covers` | ***string*** The maximum number of customers that can be sat at the table
`activity` | ***object*** object See Activity object reference
`area` | ***object*** object See Area object reference
`sort` | ***integer*** The sorting index when displaying the tables in a list
`show_to_customer` | ***string*** <code>Y/N</code> Whether the table is visible on customer facing apps

### Extra Attributes (not available on All Tables call)

Key | Description 
-------------- | --------------
`type` | ***enum*** Whether the table is a regular table or is designed to be used for PourTab or TableTab
`tab` | ***integer*** The ID of the tab currently linked to the table
`status` | ***enum*** The status of the table: <code>FREE/IN-USE</code>
`meta` | ***json*** Any additional information about the table

## All Tables

```json
{
    "success": true,
    "data": [{
      "id": 1,
      "name": "Table 01",
      "max_covers": 4,
      "activity": null,
      "area": null,
      "sort": 0,
      "show_to_customer": "Y",
  },{
      "id": 2,
      "name": "Table 02",
      "max_covers": 6,
      "activity": null,
      "area": null,
      "sort": 0,
      "show_to_customer": "Y",
  }]
}
```

This endpoint retrieves all tables

`GET https://mysite.rposcloud.com/api/table`

## Single Table

Fetches the full data for a single table

`GET https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table

## Create a Table

Creates a new table

`POST https://mysite.rposcloud.com/api/table`

## Update a Table

Updates an existing table

`PUT https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table

## Delete a Table

Deletes a table

`DELETE https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table

# Tabs

## The Tab Object

## Single Tab

## Open a new Tab

## Settle a Tab

## Close a Tab

## Unlink a Tab

## Add Item To Tab





















# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

