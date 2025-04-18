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
  "groups": [],
  "active": "Y|N",
  "created_at": "2023-03-15 09:15:00",
  "disabled_at": null,
  "expiry_date": "2024-04-27",
  "last_used": "2023-03-15 09:15:00",
  "last_used_humans": "2 months ago",
  "last_updated": "2023-03-15 09:15:00",
  "marketing_permission_given": 1,
  "promotions": [],
  "loyalty_points_balance": 0,
  "loyalty_transactions": [],
  "balance": "99.99" || null,
  "is_prepay": true || false,
  "has_open_tab": 123 || null,
  "contactInfoType": "M" || "C"
}
```

Key | Description 
-------------- | --------------
`id` | ***string*** The ID of the member
`rfid_id` | ***string*** The ID of the members' RFID card
`name` | ***string*** The name associated with the member
`avatar` | ***string*** The path to the users avatar image
`email` | ***string*** The email address associated with the member
`phone` | ***string*** The contact number of the member
`dob` | ***string*** The date of birth of the member (Format `YYYY-MM-DD`)
`additional_info` | ***object*** Array of additional information about the member (Gender, Driving license number etc)
`groups` | ***object*** List of groups the member is assigned to (See Groups section)
`active` | ***enum*** `Y/N`<br> Whether the member is activated or not (Yes - Activated/No - Deactivated)
`created_at` | ***date*** The date at which the member was created
`disabled_at` | ***date*** The date at which the member was last disabled. This is usually counted from when their most recent saved balance entry was
`expiry_date` | ***date*** The date at which the member was or will be automatically deactivated
`last_used` | ***date*** The date at which the member last used their account
`last_used_humans` | ***string*** The human friendly string describing the last used date
`marketing_permission_given` | ***bool*** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes
`promotions` | ***object*** An array of the members eligible promotions
`loyalty_points_balance` | ***int*** The number of loyalty points the member has accumulated
`loyalty_points_transactions` | ***object*** The history of loyalty transactions for the member
`balance` | ***string|null*** The current balance (credit) of the member if they are a pre pay member. Will be `null` if not using balances.
`is_prepay` | ***boolean*** A simple switch to show whether the member is a pre pay member or not
`has_open_tab` | ***int|null*** returns the `tab_id` of the active tab or null if the member doesnt have an active tab open
`contactInfoType` | ***string*** The type of entity. `M` for Member and `C` for Contact

## All Members

> All Members response

```json
// Some fields from The Member Object are omitted from the All Members endpoint

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
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"marketing_permission_given": 1
	},{
		"id": "97b1e7ec-fd18-4f0c-9f4a-fa55a5979375",
		"rfid_id": "CN97b1e7ec-fd18-4f0c-9f4a-fa55a5979375",
		"name": "Jane Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Jane",
		"email": "jane@example.com",
		"dob": "1989-04-18",
		"active": "Y",
		"created_at": "2023-03-14 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-14 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-14 09:15:00",
		"marketing_permission_given": 1
	}]
}
```

<aside class="notice">
Some fields from The Member Object are omitted from the All Members endpoint
</aside>

This endpoint retrieves All Members

`GET https://mysite.rposcloud.com/api/member`

## Single Member

> Single Member Response

```json
{
    "success": true,
    "data": {
		"id": "a7557613-12aa-472c-b341-9c951c673c99",
		"rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
		"name": "John Doe",
		"avatar": "https://upload.wikimedia.org/wikipedia/commons/thumb/5/59/User-avatar.svg/1024px-User-avatar.svg.png?20201213175635",
		"nickname": "Johnny",
		"email": "john@example.com",
		"phone": "+44123456789",
		"dob": "1988-04-18",
		"groups": [],
		"additional_info": [],
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99" || null,
		"is_prepay": true | false,
		"has_open_tab": 123
		"contactInfoType": "M"
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

```json
{
    "success": true,
    "data": {
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
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99" || null,
		"is_prepay": true | false,
		"has_open_tab": 123,
		"contactInfoType": "M"
	}
}
```

Creates a new Member

`POST https://mysite.rposcloud.com/api/member`

### Request Params

Key | Example 
-------------- | --------------
`name` | ***<span style="color:#dd4b39">required</span>*** ***string*** `John Doe`<br>The name of the Member
`email` | ***<span style="color:#dd4b39">required if passed</span>*** ***string*** `john@example.com`<br>The email address of the Member. Email is optional, however if it is passed, then it must be unique
`rfid_id` | ***<span style="color:#dd4b39">required if passed</span>*** ***string*** `CN12345678`<br>Serial number of an RFID Card. rfid_id is optional, however if it is passed, then it must be unique.
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
`is_prepay` | ***enum*** `Y/N`<br> Whether the member is a prepay member or not (Yes/No)

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
`rfid_id` | ***<span style="color:#dd4b39">required if passed</span>*** ***string*** `CN12345678`<br>Serial number of an RFID Card. rfid_id is optional, however if it is passed, then it must be unique.
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



## Upload & Update Member Avatar

> Upload & Update Member Avatar Response


```json
{
    "success": true,
    "message": "Member avatar was updated",
    "data": {
      ...MemberObject
    }
}
```

Will upload a supplied field to cloud storage, then set this as the members avatar

<aside class="notice">
You must use <code>Content-Type: multipart/form-data</code> header when sending the image file to this endpoint
</aside>

`POST https://mysite.rposcloud.com/api/member/{member_id}/upload-avatar`

### URL Params

Key | Example 
-------------- | --------------
`member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member

### Request Params

Key | Example 
-------------- | --------------
`image` | ***file*** ***<span style="color:#dd4b39">required</span>*** An uploaded file to be used for the image
