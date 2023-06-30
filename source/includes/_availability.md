# Availability

## Introduction

### Attributes

> The Availability Object

```json
{
  "success": true,
  "has_available_tables": true,
  "available_tables": [
	{
		{
            "id": 10,
            "name": "Table 01",
            "max_covers": 0,
            "activity": null,
            "area": {
                "id": 4,
                "name": "Upstairs",
                "area_settings": null,
                "show_to_customer": "Y",
                "sort": 0,
                "created_at": "2022-10-11 19:49:10",
                "updated_at": "2022-10-11 19:49:10",
                "active": "Y"
            },
            "sort": null,
            "show_to_customer": null,
            "is_available": true,
            "type": null,
            "tab": null,
            "status": null,
            "meta": null
        },
		{
            "id": 17,
            "name": "Default 03",
            "max_covers": 1,
            "activity": null,
            "area": null,
            "sort": null,
            "show_to_customer": null,
            "is_available": false,
            "type": null,
            "tab": null,
            "status": null,
            "meta": null
        },
	}
  ],
  "original_request": {
	"date": "2023-06-30 13:00",
	"covers": 1,
	"duration": 240,
	"ignoreIds": [
		"33b48075-def5-46b6-9162-960b149389c2"
	]
  },
  "min_turnaround_time": 5
}
```

Key | Description 
-------------- | --------------
`success` | ***boolean*** Whether the request was successful
`has_available_tables` | ***boolean*** Global yes/no whether there are any available tables
`available_tables` | ***array*** List of all tables [See the table object](#table-object). ***Note:*** Each table will have an extra `is_available` boolean attribute which declares wether the given table is available or not. If `tab` is not null, this indicates that a tab is currently linked to a table at the time of the request.
`original_request` | ***object*** The original request data which was sent with the request
`min_turnaround_time` | ***integer*** The `bookings::min_turnaround_time` setting which is the amount of time (in mins) that is needed between bookings on a table

## Fetch Table Availability

Fetches a list of all tables which will be either marked as available or not based on the given request data

```json
See Availability object above
```

`POST https://mysite.rposcloud.com/api/bookings/table-availability`

### Request Params

Key | Example 
-------------- | --------------
`date` | ***<span style="color:#dd4b39">required</span>*** ***string*** `2023-06-30 13:00`<br>The date and time to check availability for (YYYY-MM-DD HH:mm)
`duration` | ***<span style="color:#dd4b39">required</span>*** ***integer*** `120`<br>The amount of time in minutes of the booking
`covers` | ***<span style="color:#dd4b39">required</span>*** ***integer*** `4`<br>The number of covers/seats required for the booking
`ignoreIds` | ***array*** `['33b48075-def5-46b6-9162-960b149389c2']`<br> A list of booking ids to ignore when performing the request. This is useful for when you are wanting to check the availability for the booking you are on. It will exclude the current booking from the availability check