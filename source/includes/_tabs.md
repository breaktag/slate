<a name="tab-object"></a>
# Tabs

## The Tab Object

### Attributes

> The Tab object

```json 
{
  "id": 34212,
  "rfid_id": "G1745413345",
  "external_tab_id": "",
  "member_id": "0",
  "linked_tables": [],
  "name": "Auto Tab",
  "covers": 1,
  "tab_type": "Auto Tab",
  "category": null,
  "status": "SETTLED",
  "time_opened": "2025-04-23 14:02:25",
  "time_closed": "2025-04-23 14:02:25",
  "time_paid": "2025-04-23 14:02:25",
  "opened_by": "John Doe",
  "closed_by": "John Doe",
  "paid_by": "John Doe",
  "owner": null,
  "grand_total": 10.9,
  "sales_tax": 1.82,
  "payments_total": 10.9,
  "outstanding_total": 0,
  "items": [
      {
          "id": 82305,
          "order_id": "12",
          "tab_id": 34212,
          "item_id": 5291,
          "item_category": "DRINKS",
          "item_name": "Cappuccino",
          "quantity": "1.000",
          "quantity_multiplier": "1.00",
          "item_price": "3.900",
          "total_price": 3.9,
          "tax_item_price": 3.25,
          "total_tax_price": 3.25,
          "tax_rate": "20.00",
          "original_price": "3.90",
          "cost_price": "0.00",
          "total_cost_price": 0,
          "price_level": 1,
          "status": "NEW",
          "linked_to_promotion": null,
          "course": 2,
          "current_course": 2,
          "time_ordered": "2025-04-23 14:02:25",
          "ordered_by": "John Doe",
          "device_id": "EPOS Mini 1",
          "seq_number": "578-0000000004",
          "acknowledged_by": "",
          "acknowledged_timestamp": "0000-00-00 00:00:00",
          "ready_by": "",
          "ready_timestamp": "0000-00-00 00:00:00",
          "collected_by": "",
          "collected_timestamp": "0000-00-00 00:00:00",
          "refund_reason": "",
          "refund_by": "",
          "void_reason": "",
          "void_by": "",
          "collection": null,
          "delivery": null,
          "online_order": "N",
          "discount_id": null,
          "active": "Y",
          "hash": "5af52d20287ac41fd530fd1064c12a2692d151d6711609c057d2ce917a180c94"
      },
      {
          "id": 82306,
          "order_id": "12",
          "tab_id": 34212,
          "item_id": 5299,
          "item_category": "FOOD",
          "item_name": "Croissant",
          "quantity": "1.000",
          "quantity_multiplier": "1.00",
          "item_price": "7.000",
          "total_price": 7,
          "tax_item_price": 5.83,
          "total_tax_price": 5.83,
          "tax_rate": "20.00",
          "original_price": "7.00",
          "cost_price": "0.00",
          "total_cost_price": 0,
          "price_level": 1,
          "status": "NEW",
          "linked_to_promotion": null,
          "course": 2,
          "current_course": 2,
          "time_ordered": "2025-04-23 14:02:25",
          "ordered_by": "John Doe",
          "device_id": "EPOS Mini 1",
          "seq_number": "578-0000000005",
          "acknowledged_by": "",
          "acknowledged_timestamp": "2025-04-23 14:02:25",
          "ready_by": "",
          "ready_timestamp": "2025-04-23 14:02:25",
          "collected_by": "",
          "collected_timestamp": "2025-04-23 14:02:25",
          "refund_reason": "",
          "refund_by": "",
          "void_reason": "",
          "void_by": "",
          "collection": null,
          "delivery": null,
          "online_order": "N",
          "discount_id": null,
          "active": "Y",
          "hash": "9135f5e998169b3646a8cdcc4762864a7278d41da415aed598eca7d5760f12f3"
      }
  ],
  "payments": [
      {
          "id": 82307,
          "order_id": "12",
          "tab_id": 34212,
          "item_name": "Card Payment",
          "item_price": "-10.900",
          "tax_item_price": 0,
          "tax_rate": null,
          "status": "COMPLETE",
          "time_ordered": "2025-04-23 14:02:25",
          "ordered_by": "John Doe",
          "device_id": "EPOS Mini 1",
          "seq_number": "578-0000000006",
          "collection": null,
          "delivery": null,
          "online_order": "N",
          "active": "Y",
          "hash": "185c029db4cbd996ffdb2906be351efd1bf96eee387c65642fad0baab54c7c77"
      }
  ],
  "discounts": [],
  "promotions": [],
  "voidedItems": []
}
```

Key | Description 
-------------- | --------------
`id` | ***int*** The ID of the TAB
`rfid_id` | ***string*** The ID of the members' RFID card
`external_tab_id` | ***string*** If using an external system to link up tabs this will be the external ID of the tab
`member_id` | ***string or 0*** The Member ID of the Member the tab is linked to
`linked_tables` | ***array*** An array of tables linked to the Tab
`name` | ***string*** The name associated with the Tab
`covers` | ***int*** The number of covers the Tab is for
`tab_type` | ***string*** The type of Tab: Can be "Auto Tab", "Post Pay" or "Pre Pay"
`status` | ***enum*** <code>OPEN/CLOSED/SETTLED</code> The status of the Tab
`time_opened` | ***string*** The date and time the Tab was opened
`time_closed` | ***string*** The date and time the Tab was closed
`time_paid` | ***string*** The date and time the Tab was paid (settled)
`opened_by` | ***string*** The name of the person who opened the Tab
`closed_by` | ***string*** The name of the person who closed the Tab
`paid_by` | ***string*** The name of the person who paid the Tab
`owner` | ***string or NULL*** The name of the person who owns the Tab (usually for Tip distribution purposes)
`grand_total` | ***float*** The total amount of the Tab
`sales_tax` | ***float*** The total amount of sales tax on the Tab
`payments_total` | ***float*** The total amount of payments made on the Tab
`outstanding_total` | ***float*** The total amount outstanding on the Tab if partial payments have already been made

## Current Tabs

> Current Tabs Object

```json
[
  {
    "id": 34212,
    "rfid_id": "G1745413345",
    "external_tab_id": "",
    "member_id": "0",
    "name": "Auto Tab",
    "covers": 1,
    "tab_type": "Auto Tab",
    "category": null,
    "status": "OPEN",
    "time_opened": "2025-04-23 14:02:25",
    "time_closed": null,
    "time_paid": null,
    "opened_by": "John Doe",
    "closed_by": "John Doe",
    "paid_by": "John Doe",
    "owner": null,
    "grand_total": 10.9,
    "sales_tax": 1.82,
    "payments_total": 10.9,
    "outstanding_total": 0
  },
  {
    "id": 34213,
    "rfid_id": "G1745413345",
    "external_tab_id": "",
    "member_id": "0",
    "name": "Auto Tab",
    "covers": 1,
    "tab_type": "Auto Tab",
    "category": null,
    "status": "OPEN",
    "time_opened": "2025-04-23 14:02:25",
    "time_closed": null,
    "time_paid": null,
    "opened_by": "John Doe",
    "closed_by": "John Doe",
    "paid_by": "John Doe",
    "owner": null,
    "grand_total": 10.9,
    "sales_tax": 1.82,
    "payments_total": 10.9,
    "outstanding_total": 0
  },
  {
    "id": 34214,
    "rfid_id": "G1745413345",
    "external_tab_id": "",
    "member_id": "0",
    "name": "Auto Tab",
    "covers": 1,
    "tab_type": "Auto Tab",
    "category": null,
    "status": "OPEN",
    "time_opened": "2025-04-23 14:02:25",
    "time_closed": null,
    "time_paid": null,
    "opened_by": "John Doe",
    "closed_by": "John Doe",
    "paid_by": "John Doe",
    "owner": null,
    "grand_total": 10.9,
    "sales_tax": 1.82,
    "payments_total": 10.9,
    "outstanding_total": 0
  }
]
```

Shows a list of all current tabs. All current tabs are all tabs in the system which do not have a `status` of `SETTLED` and were opened since the last time a cash-up was run.

<aside class="notice">
Individual Line Item Resources are not included in this response. To retrieve individual line items, use the Single Tab endpoint.
</aside>

`GET https://mysite.rposcloud.com/api/tab/current`

## Single Tab

> Single tab object

```json
{
  "data": {
    "id": 34212,
    "rfid_id": "G1745413345",
    "external_tab_id": "",
    "member_id": "0",
    "linked_tables": [
      // See Table object
    ],
    "name": "Auto Tab",
    "covers": 1,
    "tab_type": "Auto Tab",
    "category": null,
    "status": "SETTLED",
    "time_opened": "2025-04-23 14:02:25",
    "time_closed": "2025-04-23 14:02:25",
    "time_paid": "2025-04-23 14:02:25",
    "opened_by": "John Doe",
    "closed_by": "John Doe",
    "paid_by": "John Doe",
    "owner": null,
    "grand_total": 10.9,
    "sales_tax": 1.82,
    "payments_total": 10.9,
    "outstanding_total": 0,
    "items": [
      // See Line Item Resources > Sale Item 
    ],
    "payments": [
        // See Line Item Resources > Payment Item 
    ],
    "discounts": [
        // See Line Item Resources > Discount Item 
    ],
    "promotions": [
        // See Line Item Resources > Promotion Item 
    ],
    "voidedItems": [
        // See Line Item Resources > Voided Item 
    ]
  },
  "success": true
}
```

Fetches the full data for a single Tab

`GET https://mysite.rposcloud.com/api/tab/{tab_id}`

### URL Params

Key | Example 
-------------- | --------------
`tab_id` | `3175` <br>The ID of the Tab

## Open a new Tab

## Settle a Tab

## Close a Tab

## Unlink a Tab

## Add Item To Tab
