# Areas

## The Area Object

Areas are locations in a venue where multiple tables can exist

### Attributes

> The Area Object

```json
{
  "id": 1,
  "name": "Upstairs",
  "sort": 0,
  "show_to_customer": "Y",
  "active": "Y"
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the Area
`name` | ***string*** The name associated of the Area
`sort` | ***integer*** The sorting index when displaying the Areas in a list
`show_to_customer` | ***string*** <code>Y/N</code> Whether the Area is visible on customer facing apps
`active` | ***string*** <code>Y/N</code> Whether the Area is active or not

## All Areas

> All Areas Response

```json
{
    "success": true,
    "data": [{
      "id": 1,
      "name": "Upstairs",
      "sort": 0,
      "show_to_customer": "Y",
      "active": "Y"
  },{
      "id": 2,
      "name": "Beer Garden",
      "sort": 1,
      "show_to_customer": "N",
      "active": "N"
  }]
}
```

This endpoint retrieves all Areas

`GET https://mysite.rposcloud.com/api/area`

## Single Area

> Single Area Response

```json
{
    "success": true,
    "data": {
      "id": 1,
      "name": "Upstairs",
      "sort": 0,
      "show_to_customer": "Y",
      "active": "Y"
    }
}
```

Fetches the full data for a single Area

`GET https://mysite.rposcloud.com/api/area/{area_id}`

### URL Params

Key | Example 
-------------- | --------------
`area_id` | `1` <br>The ID of the Area

## Create a Area

> Create Area Response

```json
{
    "success": true,
    "message": "Area was successfully created",
    "data": {
      "id": 1,
      "name": "Upstairs",
      "sort": 0,
      "show_to_customer": "Y",
      "active": "Y"
    }
}
```

Creates a new Area

`POST https://mysite.rposcloud.com/api/area`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Upstairs`<br>The name of the Area
`active` | ***enum*** `Y/N`<br> Whether the Area is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Area is visible to customer facing apps (Yes/No)
`sort`  | ***integer*** <br> Sorting number

## Update a Area

> Update Area Response

```json
{
    "success": true,
    "message": "Area was successfully updated",
    "data": {
      "id": 1,
      "name": "Upstairs",
      "sort": 0,
      "show_to_customer": "Y",
      "active": "Y"
    }
}
```

Updates an existing Area

`PUT https://mysite.rposcloud.com/api/area/{area_id}`

### URL Params

Key | Example 
-------------- | --------------
`area_id` | `1` <br>The ID of the Area

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `Upstairs`<br>The name of the Area
`active` | ***enum*** `Y/N`<br> Whether the Area is active or not (Yes/No)
`show_to_customer` | ***enum*** `Y/N`<br> Whether the Area is visible to customer facing apps (Yes/No)
`sort`  | ***integer*** <br> Sorting number

## Delete a Area

> Delete Area Response

```json
{
  "success": true,
  "message": "Area successfully deleted"
}
```

Deletes a Area

`DELETE https://mysite.rposcloud.com/api/area/{area_id}`

### URL Params

Key | Example 
-------------- | --------------
`area_id` | `1` <br>The ID of the Area