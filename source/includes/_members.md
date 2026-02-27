# Members

## The Member Object

### Attributes

> The Member Object

```json
{
  "id": "a7557613-12aa-472c-b341-9c951c673c99",
  "rfid_id": "CNa7557613-12aa-472c-b341-9c951c673c99",
  "site_id": 106,
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
  "has_expired": true || false,
  "last_used": "2023-03-15 09:15:00",
  "last_used_humans": "2 months ago",
  "last_updated": "2023-03-15 09:15:00",
  "marketing_permission_given": 1,
  "loyalty_scheme_id": "ls_2f40b321-d827-49ca-9f73-dd06d7122868",
  "loyalty_scheme": {
    "id": "ls_2f40b321-d827-49ca-9f73-dd06d7122868",
    "name": "Womens' Senior Football Team",
    "code": "WSFT",
    "group_id": "90b1cd4e-48d4-4d27-a553-2ab71a2b7f2c",
    "email_id": null,
    "wallet_pass_id": null,
    "members_count": 4,
    "active": 1
  },
  "loyalty_points_balance": 0,
  "stamp_cards": [{
    "scheme_id": "ss_b1e23b4b-a689-467b-a408-967d73decead",
    "scheme_name": "Buy 6 Pints Get Your 7th Free",
    "promotion_id": "09141a66-d85b-4f23-ba17-195add92a9bf",
    "wallet_id": "wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265",
    "theme": {
        "id": "wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265",
        "venue_logo_text": "The Test Inn",
        "image_folder": "test",
        "venue_background_color": "rgba(0, 0, 0, 255)",
        "venue_foreground_color": "rgba(255, 255, 255, 255)",
        "venue_label_color": "rgba(255, 255, 255, 255)",
        "logo_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/tabology\/logo.png",
        "strip_img_url": null,
        "icon_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/tabology\/icon.png",
        "background_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/background.png",
        "stamped_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/stamped.png",
        "unstamped_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/unstamped.png",
        "active": "1",
        "created_at": "2025-10-17 11:11:59",
        "updated_at": "2025-10-17 11:12:03",
        "deleted_at": null
    },
    "redemption_type": "1",
    "active": [
        {
            "stamp_card_id": "sc_83c8433b-132e-11f1-a75b-02a6f1544f11",
            "stamps_collected": "2",
            "stamps_required": "6"
        }
    ],
    "completed": [
      "sc_35ad26d3-4989-44d6-9674-c4abab688db1",
      "sc_e686c526-6f7f-4153-9a4f-cb05373f7a1e",
      "sc_ca8a606b-95c0-4f1b-b480-b63fd759514e"
    ]
  }],
  "balance": "99.99" || null,
  "is_prepay": true || false,
  "has_open_tab": 123 || null,
  "contactInfoType": "M" || "C",
  "promotions": [],
  "loyalty_transactions": []
}
```

| Key                           | Description                                                                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                          | **_string_** The ID of the member                                                                                                       |
| `rfid_id`                     | **_string_** The ID of the members' RFID card                                                                                           |
| `site_id`                     | **_int_** The ID of the site where the member was originally created                                                                    |
| `name`                        | **_string_** The name associated with the member                                                                                        |
| `avatar`                      | **_string_** The path to the user's avatar image                                                                                        |
| `nickname`                    | **_string_** The nickname associated with the member                                                                                    |
| `email`                       | **_string_** The email address associated with the member                                                                               |
| `phone`                       | **_string_** The contact number of the member                                                                                           |
| `dob`                         | **_string_** The date of birth of the member (Format `YYYY-MM-DD`)                                                                      |
| `additional_info`             | **_object_** Array of additional information about the member (Gender, Driving license number etc)                                      |
| `groups`                      | **_object_** List of groups the member is assigned to (See Groups section)                                                              |
| `active`                      | **_enum_** `Y/N`<br> Whether the member is activated or not (Yes - Activated/No - Deactivated)                                          |
| `created_at`                  | **_date_** The date at which the member was created                                                                                     |
| `disabled_at`                 | **_date_** The date at which the member was last disabled. This is usually counted from when their most recent saved balance entry was  |
| `expiry_date`                 | **_date_** The date at which the member was or will be automatically deactivated                                                        |
| `has_expired`                 | **_bool_** `true/false` whether the member is expired                                                                                   |
| `last_used`                   | **_date_** The date at which the member last used their account                                                                         |
| `last_used_humans`            | **_string_** The human friendly string describing the last used date                                                                    |
| `last_updated`                | **_date_** The date at which the member record was last updated                                                                         |
| `marketing_permission_given`  | **_bool_** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes                        |
| `loyalty_scheme_id`           | **_string_** The ID of the loyalty scheme of which the member first signed up                                                           |
| `loyalty_scheme`              | **_object_** The full object for the loyalty scheme of which the member first signed up                                                 |
| `loyalty_points_balance`      | **_int_** The number of loyalty points the member has accumulated                                                                       |
| `stamp_cards`                 | **_array_** An array of Stamp Card Schemes assigned to the member [See the member stamp cards object](#the-member-stamp-cards-object)    |
| `balance`                     | **_string_** or `null` The current balance (credit) of the member if they are a pre pay member. Will be `null` if not using balances.   |
| `is_prepay`                   | **_boolean_** A simple switch to show whether the member is a pre pay member or not                                                     |
| `has_open_tab`                | **_int_** or `null` returns the `tab_id` of the active tab or null if the member doesn't have an active tab                             |
| `contactInfoType`             | **_string_** The type of entity. `M` for Member and `C` for Contact                                                                     |
| `promotions`                  | **_array_** An array of the member's eligible promotions                                                                                |
| `loyalty_transactions`        | **_array_** The history of loyalty transactions for the member                                                                          |

## The Member Stamp Cards Object

### Attributes

> The Member Stamp Cards Object

```json
{
  ...
  "stamp_cards": [{
    "scheme_id": "ss_b1e23b4b-a689-467b-a408-967d73decead",
    "scheme_name": "Buy 6 Pints Get Your 7th Free",
    "promotion_id": "09141a66-d85b-4f23-ba17-195add92a9bf",
    "wallet_id": "wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265",
    "theme": {
        "id": "wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265",
        "venue_logo_text": "The Test Inn",
        "image_folder": "test",
        "venue_background_color": "rgba(0, 0, 0, 255)",
        "venue_foreground_color": "rgba(255, 255, 255, 255)",
        "venue_label_color": "rgba(255, 255, 255, 255)",
        "logo_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/tabology\/logo.png",
        "strip_img_url": null,
        "icon_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/tabology\/icon.png",
        "background_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/background.png",
        "stamped_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/stamped.png",
        "unstamped_img_url": "https:\/\/tabology-images.s3.eu-west-1.amazonaws.com\/wallet-passes\/test\/wp_b47c8d3a-41ce-4d92-8e35-a61f3c7fc265\/unstamped.png",
        "active": "1",
        "created_at": "2025-10-17 11:11:59",
        "updated_at": "2025-10-17 11:12:03",
        "deleted_at": null
    },
    "redemption_type": "1",
    "active": [
        {
            "stamp_card_id": "sc_83c8433b-132e-11f1-a75b-02a6f1544f11",
            "stamps_collected": "2",
            "stamps_required": "6"
        }
    ],
    "completed": [
      "sc_35ad26d3-4989-44d6-9674-c4abab688db1",
      "sc_e686c526-6f7f-4153-9a4f-cb05373f7a1e",
      "sc_ca8a606b-95c0-4f1b-b480-b63fd759514e"
    ]
  }]
}
```

A member may be assigned to one or many **Stamp Card Schemes**. For each **Stamp Card Scheme**, the object attributes are described below:

| Key               | Description                                                                                                                                                                                                                                                                                                                                                                                         |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `scheme_id`       | **_string_** The ID of the Stamp Card Scheme                                                                                                                                                                                                                                                                                                                                                        |
| `scheme_name`     | **_string_** The name of the Stamp Card Scheme                                                                                                                                                                                                                                                                                                                                                      |
| `promotion_id`    | **_string_** The ID of the promotion the Stamp Card Scheme is linked to                                                                                                                                                                                                                                                                                                                             |
| `wallet_id`       | **_string_** The ID of the wallet pass the Stamp Card Scheme is linked to                                                                                                                                                                                                                                                                                                                           |
| `theme`           | **_object_** The themed attributes of the wallet pass. (Such as colours, images, logos, stamps etc )                                                                                                                                                                                                                                                                                                |
| `redemption_type` | **_enum_** Redemption method (`1`: **Redeem for the cheapest product**, `2`: **Redeem for the most expensive product**)                                                                                                                                                                                                                                                                             |
| `active`          | **_array_** An array of any active (partially complete) Stamp Card objects. Each Stamp Card will show <br> `stamp_card_id` - The ID of the stamp card, <br>`stamps_collected` - The number of stamps currently collected on the Stamp Card, <br>`stamps_required` - The number of stamps required for a full Stamp Card. <br> Once a stamp card is full it moves into the completed section (below) |
| `completed`       | **_array_** An array of all completed Stamp Card IDs for this Stamp Card Scheme                                                                                                                                                                                                                                                                                                                     |

## All Members

> All Members response

```json
// Some fields from The Member Object are omitted from the All Members endpoint

{
  "success": true,
  "data": [
    {
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
    },
    {
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
    }
  ]
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
		"has_expired": false,
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99" || null,
		"is_prepay": true || false,
		"has_open_tab": 123,
		"contactInfoType": "M"
	}
}
```

Fetches the full data for a single Member

`GET https://mysite.rposcloud.com/api/member/{member_id}`

### URL Params

| Key         | Example                                                           |
| ----------- | ----------------------------------------------------------------- |
| `member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member |

## Single Members' Tabs

Fetches the most recent list of tabs for a single member

`GET https://mysite.rposcloud.com/api/member/{member_id}/tabs`

### URL Params

| Key         | Example                                                           |
| ----------- | ----------------------------------------------------------------- |
| `member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member |

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
		"groups": [],
		"active": "Y",
		"created_at": "2023-03-15 09:15:00",
		"disabled_at": null,
		"expiry_date": "2024-04-27",
		"has_expired": false,
		"last_used": "2023-03-15 09:15:00",
		"last_used_humans": "2 months ago",
		"last_updated": "2023-03-15 09:15:00",
		"marketing_permission_given": 1,
		"promotions": [],
		"loyalty_points_balance": 0,
		"loyalty_transactions": [],
		"balance": "99.99" || null,
		"is_prepay": true || false,
		"has_open_tab": 123,
		"contactInfoType": "M"
	}
}
```

Creates a new Member

`POST https://mysite.rposcloud.com/api/member`

### Request Params

| Key                          | Example                                                                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                       | **_<span style="color:#dd4b39">required</span>_** **_string_** `John Doe`<br>The name of the Member                                                                                                            |
| `email`                      | **_<span style="color:#dd4b39">required if passed</span>_** **_string_** `john@example.com`<br>The email address of the Member. Email is optional, however if it is passed, then it must be unique             |
| `rfid_id`                    | **_<span style="color:#dd4b39">required if passed</span>_** **_string_** `CN12345678`<br>Serial number of an RFID Card. rfid_id is optional, however if it is passed, then it must be unique.                  |
| `dob`                        | **_date_** `YYYY-MM-DD`<br> The member's date of birth. Must match format                                                                                                                                      |
| `phone`                      | **_string_** `+441234567890`<br>The phone number of the Member                                                                                                                                                 |
| `nickname`                   | **_string_** `Johnny`<br>The nickname of the Member                                                                                                                                                            |
| `avatar`                     | **_string_** `https://example.com/avatar.png`<br>The avatar image url for the Member                                                                                                                           |
| `expiry_date`                | **_date_** `2029-01-01`<br>The expiry date of the Member                                                                                                                                                       |
| `marketing_permission_given` | **_bool_** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes                                                                                               |
| `loyalty_scheme_code`        | **_string_** `STUDENT23`<br>A code to link to a Loyalty Scheme ID                                                                                                                                              |
| `loyalty_scheme_id`          | **_string_** `ls_86df7031-28f4-4974-81fd-231c8f1f1dad`<br>An ID of a valid Loyalty Scheme                                                                                                                      |
| `password`                   | **_string_** If using member registration then a password can be set                                                                                                                                           |
| `password_confirmation`      | **_string_** If using member registration then a password can be set and must be confirmed and match the same as the above. This is **_<span style="color:#dd4b39">required</span>_** if specifying a password |
| `is_prepay`                  | **_enum_** `Y/N`<br> Whether the member is a prepay member or not (Yes/No)                                                                                                                                     |

## Update a Member

> Update a Member Response

```json
#
```

Updates an existing Member

`PUT https://mysite.rposcloud.com/api/member/{member_id}`

### URL Params

| Key         | Example                                                           |
| ----------- | ----------------------------------------------------------------- |
| `member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member |

### Request Params

| Key                          | Example                                                                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `name`                       | **_<span style="color:#dd4b39">required</span>_** **_string_** `John Doe`<br>The name of the Member                                                                                                            |
| `rfid_id`                    | **_<span style="color:#dd4b39">required if passed</span>_** **_string_** `CN12345678`<br>Serial number of an RFID Card. rfid_id is optional, however if it is passed, then it must be unique.                  |
| `dob`                        | **_date_** `YYYY-MM-DD`<br> The member's date of birth. Must match format                                                                                                                                      |
| `phone`                      | **_string_** `+441234567890`<br>The phone number of the Member                                                                                                                                                 |
| `nickname`                   | **_string_** `Johnny`<br>The nickname of the Member                                                                                                                                                            |
| `avatar`                     | **_string_** `https://example.com/avatar.png`<br>The avatar image url for the Member                                                                                                                           |
| `expiry_date`                | **_date_** `2029-01-01`<br>The expiry date of the Member                                                                                                                                                       |
| `marketing_permission_given` | **_bool_** `1/0` Whether or not the member has given permission to be contacted via email for marketing purposes                                                                                               |
| `password`                   | **_string_** If using member registration then a password can be set                                                                                                                                           |
| `password_confirmation`      | **_string_** If using member registration then a password can be set and must be confirmed and match the same as the above. This is **_<span style="color:#dd4b39">required</span>_** if specifying a password |

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

Updates a Member's Avatar

`PUT https://mysite.rposcloud.com/api/member/{member_id}/update-avatar`

### URL Params

| Key         | Example                                                           |
| ----------- | ----------------------------------------------------------------- |
| `member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member |

### Request Params

| Key     | Example                                                                                                                                |
| ------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `image` | **_string_** **_<span style="color:#dd4b39">required</span>_** `https://example.com/avatar.png`<br>The avatar image url for the Member |

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

Uploads a supplied file to cloud storage, then sets it as the member's avatar

<aside class="notice">
You must use <code>Content-Type: multipart/form-data</code> header when sending the image file to this endpoint
</aside>

`POST https://mysite.rposcloud.com/api/member/{member_id}/upload-avatar`

### URL Params

| Key         | Example                                                           |
| ----------- | ----------------------------------------------------------------- |
| `member_id` | `a7557613-12aa-472c-b341-9c951c673c99` <br>The UUID of the Member |

### Request Params

| Key     | Example                                                                                                |
| ------- | ------------------------------------------------------------------------------------------------------ |
| `image` | **_file_** **_<span style="color:#dd4b39">required</span>_** An uploaded file to be used for the image |
