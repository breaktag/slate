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

> All Tables Response

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

> Single Table Response

```json
{
    "success": true,
    "data": {
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
}
```

Fetches the full data for a single table

`GET https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table

## Create a Table

> Create Table Response

```json
{
    "success": true,
    "message": "Table was successfully created",
    "data": {
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
}
```

Creates a new table

`POST https://mysite.rposcloud.com/api/table`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Table 01`<br>The name of the table
`max_covers` | ***numeric*** `2`<br>The maximum number of covers for the table
`active` | ***enum*** `Y/N`<br> Whether the table is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the table is visible to customer facing apps (Yes/No)
`area` | ***integer*** `4`<br> The `ID` of a valid `Area` to attach to the table

## Update a Table

> Update Table Response

```json
{
    "success": true,
    "message": "Table was successfully updated",
    "data": {
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
}
```

Updates an existing table

`PUT https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Table 01`<br>The name of the table
`max_covers` | ***numeric*** `2`<br>The maximum number of covers for the table
`active` | ***enum*** `Y/N`<br> Whether the table is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the table is visible to customer facing apps (Yes/No)
`area` | ***integer*** `4`<br> The `ID` of a valid `Area` to attach to the table

## Delete a Table

> Delete Table Response

```json
{
  "success": true,
  "message": "Table successfully deleted"
}
```

Deletes a table

`DELETE https://mysite.rposcloud.com/api/table/{table_id}`

### URL Params

Key | Example 
-------------- | --------------
`table_id` | `1` <br>The ID of the table