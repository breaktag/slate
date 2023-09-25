# Booking Types (Activities)

## The Booking Types (Activities) Object

Activities are a way of categorising your bookings (such as names of service times: "Brunch", "Dinner" etc. Or other activities the venue might offer: "Shuffleboard", "Camping"). Activities are linked to one or more tables and can be linked to a service times set to control booking times.

<!-- Booking Types (sometimes known as Activities) are a way of categorising your bookings (such as names of service times or certain activities). Booking Types can be linked to specific tables and a Service Time set so that when making a booking the user is only presented with the various tables and times they are able to book when using realtime availability -->

### Attributes

> The Activity Object

```json
{
  "id": 1,
  "name": "Bowling",
  "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
  "tables": [{
    "id": 1,
    "name": "Bowling Alley 1"
  },{
    "id": 2,
    "name": "Bowling Alley 2"
  }],
  "show_to_customer": "Y",
  "sort": 0,
  "active": "Y"
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the Activity
`name` | ***string*** The name of the Activity
`service_time_id` | ***string*** The ID of the associated Service Time
`tables` | ***array*** An array of tables linked to the Activity
`sort` | ***integer*** The sorting index when displaying the Activities in a list
`show_to_customer` | ***string*** <code>Y/N</code> Whether the Activity is visible on customer facing apps
`active` | ***string*** <code>Y/N</code> Whether the Activity is active or not

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
      "sort": 0,
      "active": "Y"
  },{
      "id": 2,
      "name": "Bowling",
      "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
      "sort": 2,
      "show_to_customer": "N",
      "active": "N"
  },{
      "id": 3,
      "name": "Camping",
      "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
      "sort": 3,
      "show_to_customer": "N",
      "active": "N"
  }]
}
```

This endpoint retrieves all Activities

`GET https://mysite.rposcloud.com/api/activity`

## Single Booking Type (Activity)

> Single Activity Response

```json
{
  "id": 1,
  "name": "Bowling",
  "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
  "sort": 0,
  "tables": [{
    "id": 1,
    "name": "Bowling Alley 1"
  },{
    "id": 2,
    "name": "Bowling Alley 2"
  }],
  "show_to_customer": "Y",
  "active": "Y"
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
        "id": 2,
        "name": "Lunch Service",
        "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
        "show_to_customer": "Y",
        "sort": 0,
        "tables": [{
          "id": 99,
          "name": "Cafe Table 1"
        },{
          "id": 100,
          "name": "Cafe Table 2"
        }],
        "active": "Y"
    }
}
```

Creates a new Activity

`POST https://mysite.rposcloud.com/api/activity`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Lunch Service`<br>The name of the Activity
`service_time_id` | ***string***<br> An ID of a valid service time set
`tables` | ***array*** `[{id: 99, name: "Cafe Table 1"}, {id: 100, name: "Cafe Table 2"}]` <br> A json array of valid Table IDs and Names
`active` | ***enum*** `Y/N`<br> Whether the Activity is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Activity is visible to customer facing apps (Yes/No)
`sort`  | ***integer*** <br> Sorting number

## Update a Booking Type (Activity)

> Update Activity Response

```json
{
    "success": true,
    "message": "Activity was successfully updated",
    "data": {
        "id": 2,
        "name": "Lunch Service",
        "service_time_id": "st_71d67cc8-79f6-11ec-992a-ee96f29780e6",
        "show_to_customer": "Y",
        "sort": 0,
        "tables": [{
          "id": 99,
          "name": "Cafe Table 1"
        },{
          "id": 100,
          "name": "Cafe Table 2"
        }],
        "active": "Y"
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
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Lunch Service`<br>The name of the Activity
`service_time_id` | ***string***<br> An ID of a valid service time set
`tables` | ***array*** `[{id: 99, name: "Cafe Table 1"}, {id: 100, name: "Cafe Table 2"}]` <br> A json array of valid Table IDs and Names
`active` | ***enum*** `Y/N`<br> Whether the Activity is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Activity is visible to customer facing apps (Yes/No)
`sort`  | ***integer*** <br> Sorting number

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
        {
            "id": 16,
            "name": "Breakfast",
            "service_time_id": "st_3781abaf-4969-4678-b8d6-7981e631b188",
            "show_to_customer": "Y",
            "sort": 0,
            "active": "Y",
            "$isDisabled": true,
            "service_times_json": [
                {
                    "dayOfWeek": "Wednesday",
                    "opens": "09:00",
                    "closes": "11:30"
                },
                {
                    "dayOfWeek": "Thursday",
                    "opens": "09:00",
                    "closes": "11:30"
                },
                {
                    "dayOfWeek": "Friday",
                    "opens": "09:00",
                    "closes": "11:30"
                },
                {
                    "dayOfWeek": "Friday",
                    "opens": "21:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Saturday",
                    "opens": "09:00",
                    "closes": "11:30"
                }
            ]
        },
        {
            "id": 18,
            "name": "Bowling",
            "service_time_id": "st_d83d8516-8c22-4d99-b990-18468d3ff256",
            "show_to_customer": "Y",
            "sort": 0,
            "active": "Y",
            "$isDisabled": false,
            "service_times_json": [
                {
                    "dayOfWeek": "Monday",
                    "opens": "09:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Tuesday",
                    "opens": "09:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Wednesday",
                    "opens": "19:00",
                    "closes": "23:00"
                }
            ]
        },
        {
            "id": 17,
            "name": "Lunch",
            "service_time_id": null,
            "show_to_customer": "Y",
            "sort": 1,
            "active": "Y",
            "$isDisabled": false,
            "service_times_json": null
        },
        {
            "id": 14,
            "name": "Dinner",
            "service_time_id": "st_f654ca18-49bf-42d7-828e-3dbd644be9dd",
            "show_to_customer": "Y",
            "sort": 2,
            "active": "Y",
            "$isDisabled": true,
            "service_times_json": [
                {
                    "dayOfWeek": "Monday",
                    "opens": "17:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Tuesday",
                    "opens": "17:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Wednesday",
                    "opens": "17:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Thursday",
                    "opens": "17:00",
                    "closes": "23:00"
                },
                {
                    "dayOfWeek": "Friday",
                    "opens": "17:00",
                    "closes": "23:00"
                }
            ]
        }
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