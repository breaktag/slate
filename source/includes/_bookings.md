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
  "start_time": "13:30",
  "end_time": "14:57",
  "duration": 360,
  "covers": 6,
  "source": "EPOS",
  "linked_member_id": null,
  "linked_contact_id": null,
  "marketing_opt_in": 1,
  "tables": [...],
  "deposit_tab": 7,
  "tab":null,
  "tab_status": null,
  "created_by": "John Manager",
  "created_on": "2019-10-20",
  "updated_by": "John Manager",
  "updated_on": "2019-10-20",
  "notes": "allergic to shellfish",
  "private_notes": "High Priority Customer",
  "confirmed": "Y",
  "walk_in": 0,
  "has_pre_orders": false,
  "pre_order_link": null,
  "has_pre_auths": false,
  "dmn": false,
  "activity_id": null,
  "deposit_amount": 100,
  "deposit_spent": 9.99,
  "deposit_remaining": 90.01,
  "member": {...},
  "deposit_payments": [],
  "tab_saved_balances": [],
  "deposit_saved_balances": [],
  "deposit_links": []
}
```

| Key                 | Description                                                                                                                                                                            |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                | **_string_** The ID of the booking                                                                                                                                                     |
| `name`              | **_string_** The name associated with the booking                                                                                                                                      |
| `phone`             | **_string_** The telephone number associated with the booking                                                                                                                          |
| `email`             | **_string_** The email address associated with the booking                                                                                                                             |
| `date`              | **_string_** The date and time of the booking (Format `YYYY-MM-DD HH:mm`)                                                                                                              |
| `start_time`        | **_string_** The start time of the booking (Format `HH:mm`)                                                                                                                            |
| `end_time`          | **_string_** The actual end time of the booking. This will be calculated when a booking is marked as departed. Will also set the duration to match the real duration. (Format `HH:mm`) |
| `duration`          | **_int_** The duration of the booking (in minutes)                                                                                                                                     |
| `covers`            | **_int_** The number of covers for the booking                                                                                                                                         |
| `linked_member_id`  | **_string_** The member ID that the booking is linked to                                                                                                                               |
| `linked_contact_id` | **_string_** The contact ID that the booking is linked to                                                                                                                              |
| `marketing_opt_in`  | **_bool_** `1/0` Whether or not the person has given permission to be contacted via email for marketing purposes                                                                       |
| `tables`            | **_array_** [See the table object](#the-table-object)                                                                                                                                  |
| `deposit_tab`       | **_int_** the ID of the tab containing the deposit                                                                                                                                     |
| `tab`               | **_int_** the ID of the tab once booking has arrived                                                                                                                                   |
| `tab_status`        | **_int_** The status of the Tab (after marking as arrived) <br> `OPEN` - Tab is open/active <br> `Closed` -Tab is closed <br> `SETTLED` - Tab is settled at £0                         |
| `has_pre_orders`    | **_bool_** `true/false` Whether or not the booking has any pre-orders                                                                                                                  |
| `pre_order_link`    | **_string_** The link to the pre-order page                                                                                                                                            |
| `has_pre_auths`     | **_bool_** `true/false` Whether or not the booking has any pre-authorised deposits                                                                                                     |
| `dmn`               | **_bool_** `true/false` Whether or not the booking is pulled from DMN                                                                                                                  |
| `activity_id`       | **_string_** The ID of the activity that the booking is linked to                                                                                                                      |
| `created_by`        | **_string_** The user who created the booking                                                                                                                                          |
| `created_on`        | **_date_** The date at which the booking was created                                                                                                                                   |
| `notes`             | **_string_** Any optional notes attached to the booking, such as special requests or allergy notices                                                                                   |
| `private_notes`     | **_string_** Any private notes attached to the booking, such as special requests or allergy notices. Not visible to the customer.                                                      |
| `confirmed`         | **_string_** The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled<br> `N` - No Show                                         |
| `walk_in`           | **_bool_** `1/0` Whether or not the booking is a walk in                                                                                                                               |

### Extra Attributes (not available on All Bookings call)

| Key                      | Description                                                                                                                                |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| `source`                 | **_string_** The source of the booking                                                                                                     |
| `updated_by`             | **_string_** The user who created the booking                                                                                              |
| `updated_on`             | **_date_** The date at which the booking was created                                                                                       |
| `deposit_amount`         | **_float_** The total amount of deposit for the booking <br> **_note:_** _This is not available on the All Bookings endpoint_              |
| `deposit_spent`          | **_float_** The total amount of deposit spent on the booking tab <br> **_note:_** _This is not available on the All Bookings endpoint_     |
| `deposit_remaining`      | **_float_** The total amount of deposit remaining on the booking tab <br> **_note:_** _This is not available on the All Bookings endpoint_ |
| `member`                 | **_object_** [See the member object](#the-member-object) <br> **_note:_** _This is not available on the All Bookings endpoint_             |
| `deposit_payments`       | **_array_** See the ordered item object (Coming soon)<br> **_note:_** _This is not available on the All Bookings endpoint_                 |
| `tab_saved_balances`     | **_array_** See the saved balance object (Coming soon)<br> **_note:_** _This is not available on the All Bookings endpoint_                |
| `deposit_saved_balances` | **_array_** See the saved balance object (Coming soon)<br> **_note:_** _This is not available on the All Bookings endpoint_`deposit_links` | **_array_** See the deposit links object (Coming soon)<br> **_note:_** _This is not available on the All Bookings endpoint_ |

## All Bookings

> All Bookings Response

```json
{
    "success": true,
    "data": [{
        "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
        "name": "Ben Riley",
        "phone": "+441234567890",
        "email": "team@tabology.com",
        "date": "2019-10-17 15:23",
        "start_time": "15:23",
        "end_time": "16:57",
        "duration": 240,
        "covers": 3,
        "linked_member_id": null,
        "linked_contact_id": "b217a949-f49f-4d2a-bd9f-78d246b05174",
        "marketing_opt_in": 1,
        "tables": [...],
        "deposit_tab": 18071,
        "tab": 18072,
        "tab_status": "OPEN",
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
        "covers": 6,
        "linked_member_id": null,
        "linked_contact_id": "b217a949-f49f-4d2a-bd9f-78d246b05174",
        "marketing_opt_in": 1,
        "tables": [...],
        "deposit_tab": 18071,
        "tab": 18072,
        "tab_status": "OPEN",
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

| Key    | Example                                                      |
| ------ | ------------------------------------------------------------ |
| `on`   | `2022-01-01` <br>Show bookings on this date                  |
| `from` | `2022-01-01` <br>Show bookings on this date and the future   |
| `to`   | `2022-01-01` <br>Show bookings before this date and the past |

## Single Booking

> Single Booking Response

```json
{
    "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
    "name": "John doe",
    "email": "john@example.com",
    "phone": "07891234567",
    "date": "2019-10-17 15:23",
    "start_time": "15:23",
    "end_time": "16:57",
    "duration": 240,
    "covers": 3,
    "source": "Website",
    "linked_member_id": null,
    "linked_contact_id": "b217a949-f49f-4d2a-bd9f-78d246b05174",
    "marketing_opt_in": 1,
    "tables": [...],
    "deposit_tab": 6,
    "tab": null,
    "tab_status": null,
    "created_by": "John Manager",
    "created_on": "2019-10-17 15:23:53",
    "notes": "Allergic to eggs",
    "private_notes": "",
    "confirmed": "Y",
    "walk_in": 0,
    "has_pre_orders": false,
    "pre_order_link": null,
    "has_pre_auths": false,
    "dmn": false,
    "activity_id": null,
    "updated_by": "Jane FOH",
    "updated_on": "2019-10-17 15:23:53",
    "deposit_amount": 20,
    "deposit_spent": 5,
    "deposit_remaining": 15,
    "member": {...},
    "deposit_payments": [...],
    "deposit_saved_balances": [...],
    "deposit_links": [...]
}
```

Fetches the full data for a single booking

`GET https://mysite.rposcloud.com/api/bookings/{booking_id}`

### URL Params

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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
      "start_time": "15:23",
      "end_time": "16:57",
      "duration": 240,
      "covers": 3,
      "source": "Website",
      "tables": [...],
      "deposit_tab": 6,
      "tab": null,
      "tab_status": null,
      "created_by": "John Manager",
      "created_on": "2019-10-17 15:23:53",
      "notes": "Allergic to eggs",
      "private_notes": "",
      "confirmed": "Y",
      "walk_in": 0,
      "has_pre_orders": false,
      "pre_order_link": null,
      "has_pre_auths": false,
      "dmn": false,
      "activity_id": null,
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

| Key                | Example                                                                                                                                                                                                                                                                                  |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`             | **_<span style="color:#dd4b39">required</span>_** **_string_** `John Doe`<br>The name associated with the booking                                                                                                                                                                        |
| `email`            | **_<span style="color:#dd4b39">required</span>_** **_string_** `john@example.com`<br>The email address associated with the booking                                                                                                                                                       |
| `date`             | **_<span style="color:#dd4b39">required</span>_** **_string_** `2022-01-01 17:15`<br>The date and time of the booking (Format `YYYY-MM-DD HH:mm`)                                                                                                                                        |
| `phone`            | **_string_** `+441234567890`<br>The telephone number associated with the booking                                                                                                                                                                                                         |
| `duration`         | **_int_** `120`<br>The duration of the booking (in minutes)                                                                                                                                                                                                                              |
| `covers`           | **_int_** `6`<br>The number of covers for the booking                                                                                                                                                                                                                                    |
| `marketing_opt_in` | **_bool_** `1/0` Whether or not the person has given permission to be contacted via email for marketing purposes                                                                                                                                                                         |
| `tables`           | **_object_** `[]`<br>See Tables object reference                                                                                                                                                                                                                                         |
| `notes`            | **_string_** `Can we have a baby high chair`<br>Any optional notes attached to the booking, such as special requests or allergy notices                                                                                                                                                  |
| `deposit_amount`   | **_float_** `150.00`<br> Adds an initial deposit to the booking                                                                                                                                                                                                                          |
| `deposit_type`     | **_string_** `Cash`<br> Must be a valid credit line type                                                                                                                                                                                                                                 |
| `confirmed`        | **_string_** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> `N` - No Show <br> **_note:_** _This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created_ |
| `walk_in`          | **_bool_** `1/0`<br> Whether or not the booking is a walk-in                                                                                                                                                                                                                             |
| `source`           | **_string_** <br>The source of the booking                                                                                                                                                                                                                                               |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

### Request Params

| Key                | Example                                                                                                                                                                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`             | **_<span style="color:#dd4b39">required</span>_** **_string_** `John Doe`<br>The name associated with the booking                                                                                                                                                                       |
| `email`            | **_<span style="color:#dd4b39">required</span>_** **_string_** `john@example.com`<br>The email address associated with the booking                                                                                                                                                      |
| `date`             | **_<span style="color:#dd4b39">required</span>_** **_string_** `2022-01-01 17:15`<br>The date and time of the booking (Format `YYYY-MM-DD HH:mm`)                                                                                                                                       |
| `phone`            | **_string_** `+441234567890`<br>The telephone number associated with the booking                                                                                                                                                                                                        |
| `duration`         | **_int_** `120`<br>The duration of the booking (in minutes)                                                                                                                                                                                                                             |
| `covers`           | **_int_** `6`<br>The number of covers for the booking                                                                                                                                                                                                                                   |
| `marketing_opt_in` | **_bool_** `1/0` Whether or not the person has given permission to be contacted via email for marketing purposes                                                                                                                                                                        |
| `tables`           | **_object_** `[]`<br>See Tables object reference                                                                                                                                                                                                                                        |
| `notes`            | **_string_** `Can we have a baby high chair`<br>Any optional notes attached to the booking, such as special requests or allergy notices                                                                                                                                                 |
| `confirmed`        | **_string_** `Y`<br> The status code of the booking <br> `R` - Requested <br> `Y` - Confirmed<br> `D` - Declined<br> `C` - Cancelled <br> `N` - No Show<br> **_note:_** _This will always be requested (R) unless permission is granted to allow auto confirmed bookings to be created_ |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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
      "start_time": "17:30",
      "end_time": "18:52",
      "duration": 240,
      "covers": 3,
      "tables": [...],
      "deposit_tab": 6,
      "tab": 7,
      "source": "EPOS",
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

_Note_: `tab` column will be populated. `tab_status` will be `OPEN`. Tab will appear on the EPOS pre loaded with the deposit, and can now have items added to it usiong the add-item API call.

`PUT https://mysite.rposcloud.com/api/bookings/{booking_id}/arrival`

### URL Params

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

### Request Params

| Key                  | Example                                                                                                                                                                                                                         |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `add_service_charge` | **_string_** <code>Y/N</code> Whether or not to add the default service charge behaviour. <br> `Y` - Default behaviour will occur <br> `N` - Service charge will be voided <br> **_note:_** _This will default to `Y` if not N_ |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

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

| Key          | Example                                                          |
| ------------ | ---------------------------------------------------------------- |
| `booking_id` | `bf3a4974-f0e9-11e9-86c3-080027d0eccd` <br>The ID of the booking |

### Request Params

| Key              | Example                                                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `deposit_amount` | **_<span style="color:#dd4b39">required</span>_** **_string_** `25`<br>The amount in (£/$/€) of the deposit to be added |
| `deposit_type`   | **_<span style="color:#dd4b39">required</span>_** **_string_** `Cash`<br> Must be a valid credit line type              |

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

| Key                  | Example                                                                                                                                |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `booking_deposit_id` | `b0d4f55f-0452-11ee-879f-02a6f1544f11` <br>The ID of the deposit (Can be found from the `deposit_links` section on the booking object) |

### Request Params

| Key              | Example                                                                                                                                  |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `deposit_amount` | **_<span style="color:#dd4b39">required</span>_** **_string_** `25`<br>The amount in (£/$/€) of the deposit to be refunded               |
| `deposit_type`   | **_<span style="color:#dd4b39">required</span>_** **_string_** `Cash`<br> Must be a valid credit line type matching the original deposit |

<aside class="notice">
Only bookings that have not been yet been marked as arrived can be refunded
</aside>

<aside class="notice">
If using deposit links, the deposit can only be refunded once the initial payment has been completed by the customer
</aside>

<aside class="warning">
If using Stripe on Mobile Ordering. It WILL refund the payment on Stripe
</aside>

## Booking History for Email

> Booking History for Email Response

```json
{
    "success": true,
    "data": [{
        "id": "bf3a4974-f0e9-11e9-86c3-080027d0eccd",
        "name": "Ian Berry",
        "phone": "+441234567890",
        "email": "team@tabology.com",
        "date": "2019-10-17 15:23",
        "duration": 240,
        "covers": 3,
        "linked_member_id": null,
        "linked_contact_id": "b217a949-f49f-4d2a-bd9f-78d246b05174",
        "marketing_opt_in": 1,
        "tables": [...],
        "deposit_tab": 18071,
        "tab": 18072,
        "tab_status": "OPEN",
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
        "covers": 6,
        "linked_member_id": null,
        "linked_contact_id": "b217a949-f49f-4d2a-bd9f-78d246b05174",
        "marketing_opt_in": 1,
        "tables": [...],
        "deposit_tab": 18071,
        "tab": 18072,
        "tab_status": "OPEN",
        "created_by": "John Manager",
        "created_on": "2019-10-20",
        "notes": "allergic to shellfish",
        "confirmed": "Y"
    }]
}
```

Shows a list of previous bookings for a given email address

`PUT https://mysite.rposcloud.com/api/bookings/{email}/history`

### URL Params

| Key     | Example                                                                       |
| ------- | ----------------------------------------------------------------------------- |
| `email` | `team@tabology.com` <br>The email address to search for the previous bookings |
