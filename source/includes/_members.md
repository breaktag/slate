# Members

## The Member Object

### Attributes

> The Member Object

```json
{
  "id": "a7557613-12aa-472c-b341-9c951c673c99",
  "rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
  "name": "John Doe",
  "avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
  "nickname": "Johnny",
  "email": "john@example.com",
  "phone": "+44123456789" ,
  "dob": "1988-04-18",
  "additional_info": [],
  "active": "Y",
  "created_at": "2023-03-15 09:15:00",
  "disabled_at": null,
  "expiry_date": "2024-04-27",
  "last_used": "2023-03-15 09:15:00",
  "last_used_humans": "2 months ago",
  "last_updated": "2023-03-15 09:15:00",
  "terms_agreed": null,
  "marketing_permission_given": 1,
  "promotions": [],
  "loyalty_points_balance": 0,
  "loyalty_transactions": [],
  "balance": "99.99"
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the member
`rfid_id` | ***string*** The ID of the members' RFID card
`name` | ***string*** The name associated with the member
`avatar` | ***string*** The path to the users avatar image
`email` | ***string*** The email address associated with the member
`dob` | ***string*** The date of birth of the member (Format `YYYY-MM-DD`)
`additional_info` | ***object*** Array of additional information about the member (Gender, Driving license number etc)
`groups` | ***object*** List of groups the member is assigned to (See Groups section)
`active` | ***enum*** `Y/N`<br> Whether the member is activated or not (Yes - Activated/No - Deactivated)
`created_at` | ***date*** The date at which the member was created
`disabled_at` | ***date*** The date at which the member was last disabled. This is usually counted from when their most recent saved balance entry was
`last_used` | ***date*** The date at which the member last used their account
`last_used_humans` | ***string*** The human friendly string describing the last used date
`terms_agreed` | ***date*** The date at which the member verified their account
`marketing_permission_given` | ***bool*** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes
`promotions` | ***object*** An array of the members eligible promotions
`loyalty_points_balance` | ***int*** The number of loyalty points the member has accumulated
`loyalty_points_transactions` | ***object*** The history of loyalty transactions for the member

## All Members

> All Members response

```json
{
    "success": true,
    "data": [{
		"id": "a7557613-12aa-472c-b341-9c951c673c99",
		"rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
		"name": "John Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Johnny",
		"email": "john@example.com",
		"phone": "+44123456789",
		"dob": "1988-04-18",
		"additional_info": [],
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"terms_agreed": null,
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99"
	},{
		"id": "97b1e7ec-fd18-4f0c-9f4a-fa55a5979375",
		"rfid_id": "CN97b1e7ec-fd18-4f0c-9f4a-fa55a5979375",
		"name": "Jane Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Jane",
		"email": "jane@example.com",
		"dob": "1989-04-18",
		"additional_info": [],
		"active": "Y",
		"created_at": "2023-03-14 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-14 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-14 09:15:00",
		"terms_agreed": null,
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99"
	}]
}
```

This endpoint retrieves All Members

`GET https://mysite.rposcloud.com/api/member`

## Single Member

> Single Member Response

```json
{
    "success": true,
    "profile": {
		"id": "a7557613-12aa-472c-b341-9c951c673c99",
		"rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
		"name": "John Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Johnny",
		"email": "john@example.com",
		"phone": "+44123456789",
		"dob": "1988-04-18",
		"additional_info": [],
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"terms_agreed": null,
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99"
	}
}
```

Fetches the full data for a single Member

`GET https://mysite.rposcloud.com/api/member/{member_id}`

### URL Params

Key | Example 
-------------- | --------------
`member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member

## Single Members' Tabs

Fetches the most recent list of tabs for a single member

`GET https://mysite.rposcloud.com/api/member/{member_id}/tabs`

### URL Params

Key | Example 
-------------- | --------------
`member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member

## Create a Member

> Create a Member Response

> Single Member Response

```json
{
    "success": true,
    "profile": {
		"id": "a7557613-12aa-472c-b341-9c951c673c99",
		"rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
		"name": "John Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Johnny",
		"email": "john@example.com",
		"phone": "+44123456789",
		"dob": "1988-04-18",
		"additional_info": [],
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"terms_agreed": null,
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99"
	}
}
```

Creates a new Member

`POST https://mysite.rposcloud.com/api/member`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name of the Member
`email` | ***<span style="color:#dd4b39">required</span>*** ***string*** `john@example.com`<br>The email address of the Member. The email address must be unique
`dob` | ***date*** `YYYY-MM-DD`<br> The members date of birth. Must match format
`phone` | ***string*** `+441234567890`<br>The phone number of the Member
`nickname` | ***string*** `Johnny`<br>The nickname of the Member
`avatar` | ***string*** `https://example.com/avatar.png`<br>The avatar image url for the Member
`expiry_date` | ***date*** `2029-01-01`<br>The expiry date of the Member
`marketing_permission_given` | ***bool*** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes
`loyalty_scheme_code` | ***string*** `STUDENT23`<br>A code to link to a Loyalty Scheme ID
`loyalty_scheme_id` | ***string*** `ls_86df7031-28f4-4974-81fd-231c8f1f1dad`<br>An ID of a valid Loyalty Scheme
`password` | ***string*** If using member registration then a password can be set
`password_confirmation` | ***string*** If using member registration then a password can be set and must be confirmed and match the same as the above. This is  ***<span style="color:#dd4b39">required</span>*** if specifying a password

## Update a Member

> Update a Member Response


```json
#
```

Updates an existing Member

`PUT https://mysite.rposcloud.com/api/member/{member_id}`

### URL Params

Key | Example 
-------------- | --------------
`member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name of the Member
`dob` | ***date*** `YYYY-MM-DD`<br> The members date of birth. Must match format
`phone` | ***string*** `+441234567890`<br>The phone number of the Member
`nickname` | ***string*** `Johnny`<br>The nickname of the Member
`avatar` | ***string*** `https://example.com/avatar.png`<br>The avatar image url for the Member
`expiry_date` | ***date*** `2029-01-01`<br>The expiry date of the Member
`marketing_permission_given` | ***bool*** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes
`password` | ***string*** If using member registration then a password can be set
`password_confirmation` | ***string*** If using member registration then a password can be set and must be confirmed and match the same as the above. This is  ***<span style="color:#dd4b39">required</span>*** if specifying a password

## Update Member Avatar

> Update Member Avatar Response


```json
{
    "success": true,
    "message": "Member avatar was updated",
    "data": {
      ...MemberObject
    }
}
```

Updates a Members Avatar

`PUT https://mysite.rposcloud.com/api/member/{member_id}/update-avatar`

### URL Params

Key | Example 
-------------- | --------------
`member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member

### Request Params

Key | Example 
-------------- | --------------
`image` | ***string*** ***<span style="color:#dd4b39">required</span>*** `https://example.com/avatar.png`<br>The avatar image url for the Member