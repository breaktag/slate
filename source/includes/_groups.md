# Groups

## The Group Object

The group object is used to combine multiple members for assignment of promotions

### Attributes

> The Group Object

```json
{
	"id": "b0c53765-b6cc-44e0-af88-1436ec91eb98",
	"name": "Gold Members",
	"description": "Gold members entitles the members to 25% off each purchase",
	"icon": "",
	"additional": [],
	"core": 0,
	"hidden": 0,
	"sort": 0,
	"active": "Y"
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the Group
`name` | ***string*** The name associated of the Group
`description` | ***string*** A description associated with the Group
`icon` | ***string*** An image URL for displaying a group icon
`additional` | ***json*** Any additional information about the Group
`core` | ***boolean*** Whether the group is a core group (Default `0`)
`hidden` | ***boolean*** Whether the group is a hidden from view on customer facing apps (Default `0`)
`sort` | ***integer*** The sorting index when displaying the Groups in a list
`active` | ***string*** <code>Y/N</code> Whether the Group is active or not

## All Groups

> All Groups response

```json
{
    "success": true,
    "data": [{
		"id": "b0c53765-b6cc-44e0-af88-1436ec91eb98",
		"name": "Gold Members",
		"description": "Gold members entitles the members to 25% off each purchase",
		"icon": "",
		"additional": [],
		"core": 0,
		"hidden": 0,
		"sort": 0,
		"active": "Y"
	},{
		"id": "b0c53765-b6cc-44e0-af88-8263ec91pd75",
		"name": "Silver Members",
		"description": "Silver members entitles the members to 10% off each purchase",
		"icon": "",
		"additional": [],
		"core": 0,
		"hidden": 0,
		"sort": 0,
		"active": "Y"
	}]
}
```

This endpoint retrieves all Groups

`GET https://mysite.rposcloud.com/api/group`

## Single Group

> Single Group Response

```json
{
    "success": true,
    "data": {
		"id": "b0c53765-b6cc-44e0-af88-1436ec91eb98",
		"name": "Gold Members",
		"description": "Gold members entitles the members to 25% off each purchase",
		"icon": "",
		"additional": [],
		"core": 0,
		"hidden": 0,
		"sort": 0,
		"active": "Y"
	}]
}
```

Fetches the full data for a single Group

`GET https://mysite.rposcloud.com/api/group/{group_id}`

### URL Params

Key | Example 
-------------- | --------------
`group_id` | `1` <br>The UUID of the Group

## Single Groups' Members

## Create a Group

## Update a Group

## Assign All Members to a Group

## Assign Single Member to a Group