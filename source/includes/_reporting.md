# Reporting

## Tips

Returns a list of tips for a a given date range

**Basic URL and parameters**

`GET https://mysite.rposcloud.com/api/reporting/tips`

`GET https://mysite.rposcloud.com/api/reporting/tips?filters%5Bdate_range%5D%5Bfrom%5D=2024-10-17 05:00:00&filters%5Bdate_range%5D%5Bto%5D=2025-04-15 10:59:59&filters%5Bgrouping%5D=device_id`

> Tips Report Example Filters

```json
[
  "filters" => [
    "date_range" => [
      "from" => "2024-10-17 05:00:00",
      "to" => "2025-04-15 10:59:59"
    ],
    "grouping" => "device_id" 
    // Can be one of "device_id", "tab.paid_by", "tab.opened_by", "tab.closed_by", "tab.owner.username"
  ]
]
```

> Tips Report Output

```json
{
    "totals": {
        "sales_total": 2006.31,
        "original_total": 2006.31,
        "cost_total": 0,
        "net_sales": 0,
        "gross_profit": 0
    },
    "breakdown": [
        ....
        {
            "sales_total": "2.000",
            "original_total": "2.000",
            "cost_total": "0.000",
            "tax": null,
            "net_sales": 0,
            "gross_profit": 0,
            "gross_profit_percentage": 0,
            "site_id": "103",
            "venue_name": "The Test Inn",
            "time_ordered": "2024-10-18 17:39:27",
            "tab_id": 30960,
            "item_name": "Tip",
            "device_id": "Joanna",
            "promotion_category": null,
            "reporting_category": "Uncategorized",
            "tab": {
                "tab_id": 30960,
                "external_tab_id": null,
                "tab_category": "MEMBER",
                "tab_name": "John Doe",
                "tab_owner": null,
                "unique_id": "CQY47HB1LF80",
                "member_id": "59dfaf58-9f3e-4980-8776-d01246e3474e",
                "covers": 1,
                "tab_type": "Member Post Pay",
                "credit_limit": null,
                "table_message": "",
                "status": "SETTLED",
                "order_pin": "",
                "time_opened": "2024-10-18 17:38:40",
                "time_closed": "2024-10-18 17:39:34",
                "opened_by": "Joanna S",
                "closed_by": "Joanna S",
                "paid_by": "Joanna S",
                "time_paid": "2024-10-18 17:39:34",
                "previous_consumption": 0,
                "consumption_limit": 4,
                "consumption_warning": "N",
                "dispense_mode": "Y",
                "show_help": "Y",
                "owner": null
            }
        }
        ....
    ]
}
```

### Totals Attributes

The below attributes are available on the `totals` object. In the context of Tips, some may not be applicable.

Key | Description 
-------------- | --------------
`sales_total` | ***float*** Total value of all the tips in the period (gross)
`original_total` | ***float*** Total value of all the tips in the period before any deductions such as promotions or discounts (gross)
`cost_total` | ***float*** Total cost value of all the tips in the period
`net_sales` | ***float*** Total value of all the tips in the period (net)
`gross_profit` | ***float*** Total gross profit of all the tips in the period

### Breakdown Attributes

The below attributes are available on the `breakdown` object. In the context of Tips, some fields may not be applicable.

Key | Description 
-------------- | --------------
`sales_total` | ***float*** Line item value of tips in the period (gross)
`original_total` | ***float*** Line item value of tips in the period  before any deductions such as promotions or discounts (gross)
`cost_total` | ***float*** *Not applicable for tips*
`tax` | ***float or NULL*** *Not applicable for tips*
`net_sales` | ***float*** *Not applicable for tips*
`gross_profit` | ***float*** *Not applicable for tips*
`gross_profit_percentage` | ***float*** *Not applicable for tips*
`site_id` | ***string or int*** The Venue ID of where the tip line was recorded
`venue_name` | ***string*** The Venue name of where the tip line was recorded
`time_ordered` | ***string*** The date and time of when the tip was recorded
`tab_id` | ***int*** The Tab ID of the tab the tip was recorded on
`item_name` | ***string*** The line item name
`device_id` | ***string*** The device ID of the device the tip was recorded on
`promotion_category` | ***string or NULL*** *Not applicable for tips*
`reporting_category` | ***string or NULL*** *Not applicable for tips*


### Tab Attributes

The below attributes are available on the `breakdown.%.tab` object. In the context of Tips, some fields may not be applicable.
This contains all the details about the Tab the tip line was recorded against.

Key | Description 
-------------- | --------------
`tab_id` | ***int*** The Tab ID of the tab the tip line was recorded on
`external_tab_id` | ***string or NULL*** If using an external system to link up tabs this will be the external ID of the tab
`tab_category` | ***string*** The category of tab e.g Member, Booking, Auto tab etc
`tab_name` | ***string*** The name of the tab
`tab_owner` | ***string or NULL*** The username of the tab owner
`unique_id` | ***string or NULL*** If linked to an Member RFID card or QR code this will be the unique_id
`member_id` | ***string or NULL*** The Member ID of the Member the tab is linked to
`covers` | ***int*** The number of covers on the tab
`tab_type` | ***string*** The type of tab e.g Post pay, Pre pay, Member, Cash, Card etc
`credit_limit` | ***float or NULL*** The credit limit of the tab
`table_message` | ***string*** The message on the table, if linked to a table
`status` | ***string*** The status of the tab e.g OPEN, CLOSED, SETTLED etc
`order_pin` | ***string*** The order pin of the tab
`time_opened` | ***string*** The date and time the tab was opened
`time_closed` | ***string*** The date and time the tab was closed
`opened_by` | ***string*** The username of the user who opened the tab
`closed_by` | ***string*** The username of the user who closed the tab
`paid_by` | ***string*** The username of the user who took payment of the tab
`time_paid` | ***string*** The date and time the tab was paid
`previous_consumption` | ***float*** The previous consumption of the tab (*for self service*)
`consumption_limit` | ***float*** The consumption limit of the tab (*for self service*)
`consumption_warning` | ***string*** Whether tab is in a state of consumption warning (*for self service*)
`dispense_mode` | ***string*** Whether the tab is in dispense mode (*for self service*)
`show_help` | ***string*** Whether the tab is in show help mode (*for self service*)
`owner` | ***string or NULL*** The owner of the tab (see user object)

## Service Charges

Returns a list of service charges for a a given date range

**Basic URL and parameters**

`GET https://mysite.rposcloud.com/api/reporting/service-charges`

`GET https://mysite.rposcloud.com/api/reporting/service-charges?filters%5Bdate_range%5D%5Bfrom%5D=2024-10-17 05:00:00&filters%5Bdate_range%5D%5Bto%5D=2025-04-15 10:59:59&filters%5Bgrouping%5D=device_id`

> Service Charges Report Example Filters

```json
[
  "filters" => [
    "date_range" => [
      "from" => "2024-10-17 05:00:00",
      "to" => "2025-04-15 10:59:59"
    ],
    "grouping" => "device_id" 
    // Can be one of "device_id", "tab.paid_by", "tab.opened_by", "tab.closed_by", "tab.owner.username"
  ]
]
```

> Service Charges Report Output

```json
{
    "totals": {
        "sales_total": 2.100,
        "original_total": 2.100,
        "cost_total": 0,
        "net_sales": 0,
        "gross_profit": 0
    },
    "breakdown": [
        ...
        {
            "sales_total": "2.100",
            "original_total": "2.100",
            "cost_total": "0.000",
            "tax": null,
            "net_sales": 0,
            "gross_profit": 0,
            "gross_profit_percentage": 0,
            "site_id": "103",
            "venue_name": "The Test Inn",
            "time_ordered": "2024-10-17 10:30:51",
            "tab_id": 30687,
            "item_name": "Service Charge (10%)",
            "device_id": null,
            "promotion_category": null,
            "reporting_category": "Uncategorized",
            "tab": {
                "tab_id": 30687,
                "external_tab_id": null,
                "tab_category": null,
                "tab_name": "Table 06",
                "tab_owner": null,
                "unique_id": "G1728729070-70459",
                "member_id": "0",
                "covers": 10,
                "tab_type": "Post Pay",
                "credit_limit": null,
                "table_message": "",
                "status": "SETTLED",
                "order_pin": "",
                "time_opened": "2024-10-12 11:31:10",
                "time_closed": "2024-10-17 10:30:50",
                "opened_by": "Lee",
                "closed_by": "Lee",
                "paid_by": "Lee",
                "time_paid": "2024-10-17 10:30:50",
                "previous_consumption": 0,
                "consumption_limit": 16,
                "consumption_warning": "N",
                "dispense_mode": "Y",
                "show_help": "Y",
                "owner": null
            }
        }
        ...
    ]
}
```

### Totals Attributes

The below attributes are available on the `totals` object. In the context of service charges, some may not be applicable.

Key | Description 
-------------- | --------------
`sales_total` | ***float*** Total value of all the service charges in the period (gross)
`original_total` | ***float*** Total value of all the service charges in the period before any deductions such as promotions or discounts (gross)
`cost_total` | ***float*** Total cost value of all the service charges in the period
`net_sales` | ***float*** Total value of all the service charges in the period (net)
`gross_profit` | ***float*** Total gross profit of all the service charges in the period

### Breakdown Attributes

The below attributes are available on the `breakdown` object. In the context of service charges, some fields may not be applicable.

Key | Description 
-------------- | --------------
`sales_total` | ***float*** Line item value of service charges in the period (gross)
`original_total` | ***float*** Line item value of service charges in the period  before any deductions such as promotions or discounts (gross)
`cost_total` | ***float*** *Not applicable for service charges*
`tax` | ***float or NULL*** *Not applicable for service charges*
`net_sales` | ***float*** *Not applicable for service charges*
`gross_profit` | ***float*** *Not applicable for service charges*
`gross_profit_percentage` | ***float*** *Not applicable for service charges*
`site_id` | ***string or int*** The Venue ID of where the service charge was recorded
`venue_name` | ***string*** The Venue name of where the service charge was recorded
`time_ordered` | ***string*** The date and time of when the service charge was recorded
`tab_id` | ***int*** The Tab ID of the tab the service charge was recorded on
`item_name` | ***string*** The line item name
`device_id` | ***string*** The device ID of the device the service charge was recorded on
`promotion_category` | ***string or NULL*** *Not applicable for service charges*
`reporting_category` | ***string or NULL*** *Not applicable for service charges*


### Tab Attributes

The below attributes are available on the `breakdown.%.tab` object. In the context of service charges, some fields may not be applicable.
This contains all the details about the Tab the service charge was recorded against.

Key | Description 
-------------- | --------------
`tab_id` | ***int*** The Tab ID of the tab the service charge was recorded on
`external_tab_id` | ***string or NULL*** If using an external system to link up tabs this will be the external ID of the tab
`tab_category` | ***string*** The category of tab e.g Member, Booking, Auto tab etc
`tab_name` | ***string*** The name of the tab
`tab_owner` | ***string or NULL*** The username of the tab owner
`unique_id` | ***string or NULL*** If linked to an Member RFID card or QR code this will be the unique_id
`member_id` | ***string or NULL*** The Member ID of the Member the tab is linked to
`covers` | ***int*** The number of covers on the tab
`tab_type` | ***string*** The type of tab e.g Post pay, Pre pay, Member, Cash, Card etc
`credit_limit` | ***float or NULL*** The credit limit of the tab
`table_message` | ***string*** The message on the table, if linked to a table
`status` | ***string*** The status of the tab e.g OPEN, CLOSED, SETTLED etc
`order_pin` | ***string*** The order pin of the tab
`time_opened` | ***string*** The date and time the tab was opened
`time_closed` | ***string*** The date and time the tab was closed
`opened_by` | ***string*** The username of the user who opened the tab
`closed_by` | ***string*** The username of the user who closed the tab
`paid_by` | ***string*** The username of the user who took payment of the tab
`time_paid` | ***string*** The date and time the tab was paid
`previous_consumption` | ***float*** The previous consumption of the tab (*for self service*)
`consumption_limit` | ***float*** The consumption limit of the tab (*for self service*)
`consumption_warning` | ***string*** Whether tab is in a state of consumption warning (*for self service*)
`dispense_mode` | ***string*** Whether the tab is in dispense mode (*for self service*)
`show_help` | ***string*** Whether the tab is in show help mode (*for self service*)
`owner` | ***string or NULL*** The owner of the tab (see user object)
