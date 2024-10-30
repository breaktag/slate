# Booking Types (Activities)

## The Booking Types (Activities) Object

Activities are a way of categorising your bookings (such as names of service times: "Brunch", "Dinner" etc. Or other activities the venue might offer: "Shuffleboard", "Camping"). Activities are linked to one or more tables and can be linked to a service times set to control booking times. 

Activities can be used to control other various aspects of booking logic such as whether to take up-front deposits, pre orders, duration, covers and restrictions on date ranges.

<!-- Booking Types (sometimes known as Activities) are a way of categorising your bookings (such as names of service times or certain activities). Booking Types can be linked to specific tables and a Service Time set so that when making a booking the user is only presented with the various tables and times they are able to book when using realtime availability -->

### Attributes

> The Activity Object

```json
{
  "id": 1,
  "name": "Bowling",
  "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
  "show_to_customer": "Y",
  "opt_in_dates": "Y",
  "show_on_rwg": "N",
  "sort": 0,
  "tables": [{
    "id": 1,
    "name": "Bowling Alley 1"
  },{
    "id": 2,
    "name": "Bowling Alley 2"
  }],
  "active": "Y",
  "never_auto_confirm": 0,
  "min_covers": 0,
  "max_covers": 0,
  "min_duration": 0,
  "max_duration": 0,
  "duration": 0,
  "duration_interval": 0,
  "duration_spacing": 0,
  "skip_deposit": "Y",
  "deposit_type": "",
  "deposit_value": "0.00",
  "can_have_pre_orders": "Y",
  "charge_for_pre_orders": "N",
  "min_notice_period": null,
  "max_notice_period": null,
  "availabilities": [{
        "id": 184,
        "activity_id": 1,
        "from_date": "2024-10-22 05:00:00",
        "to_date": "2024-11-06 05:00:00",
        "created_at": "2024-10-23 10:11:25",
        "updated_at": "2024-10-23 10:11:25",
        "deleted_at": null
    }],
  "service_times_json": null,
  "$isDisabled": true,
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the Activity
`name` | ***string*** The name of the Activity
`service_time_id` | ***string*** The ID of the associated Service Time
`show_to_customer` | ***enum*** <code>Y/N</code> Whether the Activity is visible on customer facing apps
`opt_in_dates` | ***enum*** <code>Y/N</code> Whether the Activity uses restrictive availability to inclusive or exclusive of the date ranges within the `availabilities` specified
`show_on_rwg` | ***enum*** <code>Y/N</code> Whether the Activity is visible Reserve with Google (if using integration)
`sort` | ***integer*** The sorting index when displaying the Activities in a list
`tables` | ***array*** An array of tables linked to the Activity
`active` | ***enum*** <code>Y/N</code> Whether the Activity is active or not
`never_auto_confirm` | ***integer*** Never use auto confirm for bookings on these activities
`min_covers` | ***integer*** The minimum number of covers for bookings on these activities
`max_covers` | ***integer*** The maximum number of covers for bookings on these activities
`min_duration` | ***integer*** The minimum duration for bookings on these activities
`max_duration` | ***integer*** The maximum duration for bookings on these activities
`duration` | ***integer*** The fixed duration for bookings on these activities (overrides `min_duration` and `max_duration`)
`duration_interval` | ***integer*** The gap in minutes for available bookings on these activities
`duration_spacing` | ***integer*** The gap in minutes for between available bookings on these activities
`skip_deposit` | ***enum*** <code>Y/N</code> Whether to skip the up front deposit flow for bookings on these activities
`deposit_type` | ***enum*** <code>"flat"/"cover"</code> The type of deposit for bookings on these activities. `flat` charges the amount in `deposit_value`. `cover` will charge the `deposit_value` amount multiplied by the number of covers
`deposit_value` | ***string*** The value of the deposit for bookings on these activities
`can_have_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities can have pre orders attached to them
`charge_for_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities should charge for pre orders upfront
`min_notice_period` | ***integer*** The minimum notice period in minutes for bookings on these activities
`max_notice_period` | ***integer*** The maximum notice period in minutes for bookings on these activities
`availabilities` | ***array*** An array of availability objects for the Activity
`service_times_json` | ***string*** The JSON representation of the Service Time set
`"$isDisabled"` | ***boolean*** Only applies when using the `POST /api/activity/check` endpoint. Checks whether the Activities are disabled or not for a given datetime.


## All Booking Types (Activities)

> All Activities Response

```json
{
    "success": true,
    "data": [{
      "id": 1,
      "name": "Dinner Service",
      "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
        "show_to_customer": "Y",
        "opt_in_dates": "Y",
        "show_on_rwg": "N",
        "sort": 0,
        "tables": [{
            "id": 1,
            "name": "Restaurant 1"
        },{
            "id": 2,
            "name": "Restaurant 2"
        }],
        "active": "Y",
        "never_auto_confirm": 0,
        "min_covers": 0,
        "max_covers": 0,
        "min_duration": 0,
        "max_duration": 0,
        "duration": 0,
        "duration_interval": 0,
        "duration_spacing": 0,
        "skip_deposit": "Y",
        "deposit_type": "",
        "deposit_value": "0.00",
        "can_have_pre_orders": "Y",
        "charge_for_pre_orders": "N",
        "min_notice_period": null,
        "max_notice_period": null,
        "availabilities": [{
                "id": 184,
                "activity_id": 1,
                "from_date": "2024-10-22 05:00:00",
                "to_date": "2024-11-06 05:00:00",
                "created_at": "2024-10-23 10:11:25",
                "updated_at": "2024-10-23 10:11:25",
                "deleted_at": null
            }],
        "service_times_json": null
  },{
      "id": 2,
      "name": "Bowling",
      "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
    "show_to_customer": "Y",
    "opt_in_dates": "Y",
    "show_on_rwg": "N",
    "sort": 1,
    "tables": [{
        "id": 1,
        "name": "Bowling Alley 1"
    },{
        "id": 2,
        "name": "Bowling Alley 2"
    }],
    "active": "Y",
    "never_auto_confirm": 1,
    "min_covers": 2,
    "max_covers": 12,
    "min_duration": 60,
    "max_duration": 240,
    "duration": 0,
    "duration_interval": 0,
    "duration_spacing": 0,
    "skip_deposit": "N",
    "deposit_type": "cover",
    "deposit_value": "6.00",
    "can_have_pre_orders": "Y",
    "charge_for_pre_orders": "Y",
    "min_notice_period": 60,
    "max_notice_period": 1440,
    "availabilities": [{
            "id": 184,
            "activity_id": 1,
            "from_date": "2024-10-22 05:00:00",
            "to_date": "2024-11-06 05:00:00",
            "created_at": "2024-10-23 10:11:25",
            "updated_at": "2024-10-23 10:11:25",
            "deleted_at": null
        }],
        "service_times_json": null
  },{
      "id": 3,
      "name": "Camping",
      "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
      "show_to_customer": "Y",
      "opt_in_dates": "Y",
      "show_on_rwg": "Y",
      "sort": 2,
      "tables": [{
          "id": 1,
          "name": "Campsite Field 1"
      },{
          "id": 2,
          "name": "Campsite Field 2"
      }],
      "active": "Y",
      "never_auto_confirm": 0,
      "min_covers": 1,
      "max_covers": 8,
      "min_duration": 1440,
      "max_duration": 10080,
      "duration": 1440,
      "duration_interval": 1440,
      "duration_spacing": 0,
      "skip_deposit": "N",
      "deposit_type": "flat",
      "deposit_value": "100.00",
      "can_have_pre_orders": "N",
      "charge_for_pre_orders": "N",
      "min_notice_period": 1440,
      "max_notice_period": 14400,
      "availabilities": [{
              "id": 184,
              "activity_id": 1,
              "from_date": "2024-10-22 05:00:00",
              "to_date": "2024-11-06 05:00:00",
              "created_at": "2024-10-23 10:11:25",
              "updated_at": "2024-10-23 10:11:25",
              "deleted_at": null
          }],
      "service_times_json": null
  }]
}
```

This endpoint retrieves all Activities

`GET https://mysite.rposcloud.com/api/activity`

## Single Booking Type (Activity)

> Single Activity Response

```json
{
    "id": 2,
    "name": "Bowling",
    "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
    "show_to_customer": "Y",
    "opt_in_dates": "Y",
    "show_on_rwg": "N",
    "sort": 1,
    "tables": [{
        "id": 1,
        "name": "Bowling Alley 1"
    },{
        "id": 2,
        "name": "Bowling Alley 2"
    }],
    "active": "Y",
    "never_auto_confirm": 1,
    "min_covers": 2,
    "max_covers": 12,
    "min_duration": 60,
    "max_duration": 240,
    "duration": 0,
    "duration_interval": 0,
    "duration_spacing": 0,
    "skip_deposit": "N",
    "deposit_type": "cover",
    "deposit_value": "6.00",
    "can_have_pre_orders": "Y",
    "charge_for_pre_orders": "Y",
    "min_notice_period": 60,
    "max_notice_period": 1440,
    "availabilities": [{
        "id": 184,
        "activity_id": 1,
        "from_date": "2024-10-22 05:00:00",
        "to_date": "2024-11-06 05:00:00",
        "created_at": "2024-10-23 10:11:25",
        "updated_at": "2024-10-23 10:11:25",
        "deleted_at": null
    }],
    "service_times_json": null
}
```

Fetches the full data for a single Activity

`GET https://mysite.rposcloud.com/api/activity/{activity_id}`

### URL Params

Key | Example 
-------------- | --------------
`activity_id` | `1` <br>The ID of the Activity

## Create a Booking Type (Activity)

> Create Activity Response

```json
{
    "success": true,
    "message": "Activity successfully created",
    "data": {
        "id": 6,
        "name": "Set Evening Meal",
        "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
        "show_to_customer": "Y",
        "opt_in_dates": "N",
        "show_on_rwg": "N",
        "sort": 1,
        "tables": [{
            "id": 1,
            "name": "Restaurant 1"
        },{
            "id": 2,
            "name": "Restaurant 2"
        }],
        "active": "Y",
        "never_auto_confirm": 1,
        "min_covers": 2,
        "max_covers": 8,
        "min_duration": 120,
        "max_duration": 240,
        "duration": 0,
        "duration_interval": 0,
        "duration_spacing": 0,
        "skip_deposit": "N",
        "deposit_type": "cover",
        "deposit_value": "10.00",
        "can_have_pre_orders": "N",
        "charge_for_pre_orders": "N",
        "min_notice_period": 60,
        "max_notice_period": 1440,
        "availabilities": [{
            "id": 184,
            "activity_id": 1,
            "from_date": "2024-10-22 05:00:00",
            "to_date": "2024-11-06 05:00:00",
            "created_at": "2024-10-23 10:11:25",
            "updated_at": "2024-10-23 10:11:25",
            "deleted_at": null
        }],
        "service_times_json": null
  }
}
```

Creates a new Activity

`POST https://mysite.rposcloud.com/api/activity`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Set Evening Meal`<br>The name of the Activity
`service_time_id` | ***string*** `st_71d67cc8-79f6-11ec-992a-ee96f29780e6`<br> An ID of a valid service time set
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Activity is visible to customer facing apps (Yes/No)
`opt_in_dates` | ***enum*** `Y/N`<br> Whether the Activity uses restrictive availability to inclusive or exclusive of the date ranges within the availabilities specified
`show_on_rwg` | ***enum*** <code>Y/N</code> Whether the Activity is visible Reserve with Google (if using integration)
`sort` | ***integer*** `1` The sorting index when displaying the Activities in a list
`tables` | ***array*** An array of tables linked to the Activity
`active` | ***enum*** <code>Y/N</code> Whether the Activity is active or not
`never_auto_confirm` | ***integer*** `1` <br>Never use auto confirm for bookings on these activities
`min_covers` | ***integer***  `2` <br>The minimum number of covers for bookings on these activities
`max_covers` | ***integer***  `8` <br>The maximum number of covers for bookings on these activities
`min_duration` | ***integer***  `120` <br>The minimum duration for bookings on these activities
`max_duration` | ***integer***  `240` <br>The maximum duration for bookings on these activities
`duration` | ***integer*** `0` <br>The fixed duration for bookings on these activities (overrides `min_duration` and `max_duration`)
`duration_interval` | ***integer*** `0` <br>The gap in minutes for available bookings on these activities
`duration_spacing` | ***integer*** `0` <br>The gap in minutes for between available bookings on these activities
`skip_deposit` | ***enum*** <code>Y/N</code> Whether to skip the up front deposit flow for bookings on these activities
`deposit_type` | ***enum*** <code>flat/"cover</code> The type of deposit for bookings on these activities. `flat` charges the amount in `deposit_value`. `cover` will charge the `deposit_value` amount multiplied by the number of covers
`deposit_value` | ***string*** `10.00`<br>The value of the deposit for bookings on these activities
`can_have_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities can have pre orders attached to them
`charge_for_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities should charge for pre orders upfront
`min_notice_period` | ***integer*** `60`<br>The minimum notice period in minutes for bookings on these activities
`max_notice_period` | ***integer*** `1440`<br>The maximum notice period in minutes for bookings on these activities

## Update a Booking Type (Activity)

> Update Activity Response

```json
{
    "success": true,
    "message": "Activity successfully updated",
    "data": {
        "id": 6,
        "name": "Set Evening Meal",
        "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
        "show_to_customer": "Y",
        "opt_in_dates": "N",
        "show_on_rwg": "N",
        "sort": 1,
        "tables": [{
            "id": 1,
            "name": "Restaurant 1"
        },{
            "id": 2,
            "name": "Restaurant 2"
        }],
        "active": "Y",
        "never_auto_confirm": 1,
        "min_covers": 2,
        "max_covers": 8,
        "min_duration": 120,
        "max_duration": 240,
        "duration": 0,
        "duration_interval": 0,
        "duration_spacing": 0,
        "skip_deposit": "N",
        "deposit_type": "cover",
        "deposit_value": "10.00",
        "can_have_pre_orders": "N",
        "charge_for_pre_orders": "N",
        "min_notice_period": 60,
        "max_notice_period": 1440,
        "availabilities": [{
            "id": 184,
            "activity_id": 1,
            "from_date": "2024-10-22 05:00:00",
            "to_date": "2024-11-06 05:00:00",
            "created_at": "2024-10-23 10:11:25",
            "updated_at": "2024-10-23 10:11:25",
            "deleted_at": null
        }],
        "service_times_json": null
  }
}
```

Updates an existing Activity

`PUT https://mysite.rposcloud.com/api/activity/{activity_id}`

### URL Params

Key | Example 
-------------- | --------------
`activity_id` | `1` <br>The ID of the Activity

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Set Evening Meal`<br>The name of the Activity
`service_time_id` | ***string*** `st_71d67cc8-79f6-11ec-992a-ee96f29780e6`<br> An ID of a valid service time set
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Activity is visible to customer facing apps (Yes/No)
`opt_in_dates` | ***enum*** `Y/N`<br> Whether the Activity uses restrictive availability to inclusive or exclusive of the date ranges within the availabilities specified
`show_on_rwg` | ***enum*** <code>Y/N</code> Whether the Activity is visible Reserve with Google (if using integration)
`sort` | ***integer*** `1` The sorting index when displaying the Activities in a list
`tables` | ***array*** An array of tables linked to the Activity
`active` | ***enum*** <code>Y/N</code> Whether the Activity is active or not
`never_auto_confirm` | ***integer*** `1` <br>Never use auto confirm for bookings on these activities
`min_covers` | ***integer***  `2` <br>The minimum number of covers for bookings on these activities
`max_covers` | ***integer***  `8` <br>The maximum number of covers for bookings on these activities
`min_duration` | ***integer***  `120` <br>The minimum duration for bookings on these activities
`max_duration` | ***integer***  `240` <br>The maximum duration for bookings on these activities
`duration` | ***integer*** `0` <br>The fixed duration for bookings on these activities (overrides `min_duration` and `max_duration`)
`duration_interval` | ***integer*** `0` <br>The gap in minutes for available bookings on these activities
`duration_spacing` | ***integer*** `0` <br>The gap in minutes for between available bookings on these activities
`skip_deposit` | ***enum*** <code>Y/N</code> Whether to skip the up front deposit flow for bookings on these activities
`deposit_type` | ***enum*** <code>flat/"cover</code> The type of deposit for bookings on these activities. `flat` charges the amount in `deposit_value`. `cover` will charge the `deposit_value` amount multiplied by the number of covers
`deposit_value` | ***string*** `10.00`<br>The value of the deposit for bookings on these activities
`can_have_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities can have pre orders attached to them
`charge_for_pre_orders` | ***enum*** <code>Y/N</code> Whether bookings on these activities should charge for pre orders upfront
`min_notice_period` | ***integer*** `60`<br>The minimum notice period in minutes for bookings on these activities
`max_notice_period` | ***integer*** `1440`<br>The maximum notice period in minutes for bookings on these activities

## Delete a Booking Type (Activity)

> Delete Activity Response

```json
{
  "success": true,
  "message": "Activity successfully deleted"
}
```

Deletes a Activity

`DELETE https://mysite.rposcloud.com/api/activity/{activity_id}`

### URL Params

Key | Example 
-------------- | --------------
`activity_id` | `1` <br>The ID of the Activity

## Check Valid Booking Type(s) (Activities)

> Check Valid Booking Type(s) Response

```json
{
    "success": true,
    "data": [
        ...
        {
            "id": 6,
            "name": "Set Evening Meal",
            "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
            "show_to_customer": "Y",
            "opt_in_dates": "N",
            "show_on_rwg": "N",
            "sort": 1,
            "tables": [{
                "id": 1,
                "name": "Restaurant 1"
            },{
                "id": 2,
                "name": "Restaurant 2"
            }],
            "active": "Y",
            "never_auto_confirm": 1,
            "min_covers": 2,
            "max_covers": 8,
            "min_duration": 120,
            "max_duration": 240,
            "duration": 0,
            "duration_interval": 0,
            "duration_spacing": 0,
            "skip_deposit": "N",
            "deposit_type": "cover",
            "deposit_value": "10.00",
            "can_have_pre_orders": "N",
            "charge_for_pre_orders": "N",
            "min_notice_period": 60,
            "max_notice_period": 1440,
            "availabilities": [{
                "id": 184,
                "activity_id": 1,
                "from_date": "2024-10-22 05:00:00",
                "to_date": "2024-11-06 05:00:00",
                "created_at": "2024-10-23 10:11:25",
                "updated_at": "2024-10-23 10:11:25",
                "deleted_at": null
            }],
            "$isDisabled": true,
            "service_times_json": [...Array Of ServiceTimesObjects...]
        }
        ...
    ]
}
```

Fetches all the booking types with a `$isDisabled` boolean flag, denoting whether it is available for the given date time in the request.

The `$isDisabled` is not computed through looking at existing bookings and table availability. It is computed by looking at the service times which are linked to the booking type (activity). A booking type (activity) with no service times is available at all times.

`POST https://mysite.rposcloud.com/api/activity/check-valid`

### Request Params

Key | Example 
-------------- | --------------
`datetime` | ***<span style="color:#dd4b39">required</span>*** ***string*** `2023-09-25 11:30:00`<br> The datetime to check the availability for