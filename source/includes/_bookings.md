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
`confirmed` | ***string*** The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled<br> `N` - No Show

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
`confirmed` | ***string*** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> `N` - No Show <br> ***note:*** *This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created* 


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
`confirmed` | ***string*** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> `N` - No Show<br> ***note:*** *This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created* 

## Confirm a booking

> Confirm a booking response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      ...BookingObject
      "confirmed": "Y",
    }
}
```

Confirms a booking request and sends an email to the customer

<aside class="notice">
Only booking requests (<code>"confirmed": "R"</code>) can be confirmed
</aside>

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/confirm`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

## Decline a booking

> Decline a booking response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      ...BookingObject
      "confirmed": "D",
    }
}
```

Declines a booking request and sends an email to the customer

<aside class="notice">
Only booking requests (<code>"confirmed": "R"</code>) can be declined
</aside>

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/decline`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

## Cancel a booking

> Cancel a booking response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      ...BookingObject
      "confirmed": "C",
    }
}
```

Cancels a booking and sends an email to the customer

<aside class="notice">
Only booking requests (<code>"confirmed": "R"</code>) or confirmed bookings  (<code>"confirmed": "Y"</code>) can be cancelled
</aside>

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/cancel`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

## No Show a Booking

> No Show a Booking Response

```json
{
    "success": true,
    "message": "Booking was successfully updated.",
    "data": {
      ...BookingObject
      "confirmed": "N",
    }
}
```

Marks a confirmed booking as no show.

<aside class="notice">
Only confirmed bookings (<code>"confirmed": "Y"</code>) can be marked as 'No Show'
</aside>

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/no-show`

### URL Params

Key | Example 
-------------- | --------------
`booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking

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

### Request Params

Key | Example 
-------------- | --------------
`deposit_amount` | ***<span style="color:#dd4b39">required</span>*** ***string*** `25`<br>The amount in (£/$/€) of the deposit to be added
`deposit_type` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Cash`<br> Must be a valid credit line type

<aside class="notice">
Only bookings that have not been yet been marked as arrived can have a deposit added to them
</aside>


## Refund a deposit

> Refund deposit response

```json
{
    "success": true,
    "message": "Booking deposit was refunded",
    "data": {
        "booking_deposit_id": "e3dc1541-ea97-4895-9b5c-6dd2079931a0",
        "booking_id": "d837de02-6f50-43cb-95b9-94d2495cec66",
        "payment_session_id": null,
        "payment_id": null,
        "payment_type": "Giftcard",
        "deposit_amount": "34.00",
        "completed_at": "2023-06-06 14:28:43",
        "refunded_at": "2023-06-06 14:28:56",
        "revoked_at": null,
        "created_at": "2023-06-06 14:28:43",
        "updated_at": "2023-06-06 14:28:56"
    }
}
```

Refund a deposit from a booking. Refunding a deposit does not perform the actual refunding of the payment to the customer it just marks it as refunded on Tabology and won't be counted towards the total tab deposit and cash up reports etc.



`PUT https://mysite.rposcloud.com/api/deposit/{booking_deposit_id}/refund`

### URL Params

Key | Example 
-------------- | --------------
`booking_deposit_id` | `b0d4f55f-0452-11ee-879f-02a6f1544f11` <br>The ID of the deposit (Can be found from the `deposit_links` section on the booking object)

### Request Params

Key | Example 
-------------- | --------------
`deposit_amount` | ***<span style="color:#dd4b39">required</span>*** ***string*** `25`<br>The amount in (£/$/€) of the deposit to be refunded
`deposit_type` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Cash`<br> Must be a valid credit line type matching the original deposit

<aside class="notice">
Only bookings that have not been yet been marked as arrived can be refunded
</aside>

<aside class="notice">
If using deposit links, the deposit can only be refunded once the initial payment has been completed by the customer
</aside>

<aside class="warning">
If using Stripe on Mobile Ordering. It WILL refund the payment on Stripe
</aside>