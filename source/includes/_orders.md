<a name="order-object"></a>
# Orders

## The Order Object


## Current Orders

> Current Orders Object

```json
{
    "data": [
        {
            "root_category": "WET",
            "boolean_status": "PREPARING",
            "sales_total": "4.950",
            "original_total": "4.950",
            "cost_total": "0.000",
            "tax": "20.00",
            "net_sales": 4.125,
            "tax_amount": 0.825,
            "gross_profit": 4.125,
            "gross_profit_percentage": 100,
            "ordered_item_id": 82289,
            "order_id": "5",
            "tab_id": 34212,
            "status": "NEW",
            "time_ordered": "2025-04-23 09:58:23",
            "device_id": "Lees Ipad",
            "area_id": null,
            "area_name": null,
            "table_id": null,
            "table_name": null,
            "promotion_category": null,
            "reporting_category": "Uncategorized"
        },
        {
            "root_category": "WET",
            "boolean_status": "PREPARING",
            "sales_total": "4.950",
            "original_total": "4.950",
            "cost_total": "0.000",
            "tax": "20.00",
            "net_sales": 4.125,
            "tax_amount": 0.825,
            "gross_profit": 4.125,
            "gross_profit_percentage": 100,
            "ordered_item_id": 82291,
            "order_id": "6",
            "tab_id": 34212,
            "status": "NEW",
            "time_ordered": "2025-04-23 09:59:42",
            "device_id": "Lees Ipad",
            "area_id": null,
            "area_name": null,
            "table_id": null,
            "table_name": null,
            "promotion_category": null,
            "reporting_category": "Uncategorized"
        }
    ],
    "totals": []
}
```

Shows a list of all current orders. All current orders are all orders in the system which are do not have a `boolean_status` of `COMPLETED`, `TIMER` or `PAID` and were created since the last time a cash-up was run.

<aside class="notice">
Individual Line Item Resources are not included in this response. To retrieve individual line items, use the Single Order endpoint.
</aside>

`GET https://mysite.rposcloud.com/api/order/current`


## Single Order


```json
{
    "order_id": "31_34213",
    "items": [
        // See Line Item Resources > Sale Item Object
        {
            "id": 82666,
            "external_item_id": null,
            "order_id": "31",
            "tab_id": 34213,
            "item_id": 4598,
            "item_category": "DRINKS",
            "item_name": "Syrup 1",
            "quantity": "1.000",
            "quantity_multiplier": "1.00",
            "item_price": "0.500",
            "original_price": "0.50",
            "cost_price": "0.00",
            "price_level": 1,
            "status": "NEW",
            "linked_to_item": 210422079,
            "linked_to_offer": null,
            "linked_to_promotion": null,
            "course": 2,
            "current_course": 2,
            "order_msg": null,
            "ordered_by": "John Doe",
            "device_id": "EPOS Mini 1",
            "seq_number": "036-0000000355",
            "time_ordered": "2025-04-24 13:04:10",
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
            "hash": "f41431001b416c3851e3739d921664fbcdfccd13cffb79d3ec7927b0bf86a781"
        },
        {
            "id": 82667,
            "external_item_id": null,
            "order_id": "31",
            "tab_id": 34213,
            "item_id": 5155,
            "item_category": "DRINKS",
            "item_name": "Croissant",
            "quantity": "1.000",
            "quantity_multiplier": "1.00",
            "item_price": "3.600",
            "original_price": "3.60",
            "cost_price": "0.00",
            "price_level": 1,
            "status": "NEW",
            "linked_to_item": null,
            "linked_to_offer": null,
            "linked_to_promotion": null,
            "course": 2,
            "current_course": 2,
            "order_msg": null,
            "ordered_by": "John Doe",
            "device_id": "EPOS Mini 1",
            "seq_number": "036-0000000356",
            "time_ordered": "2025-04-24 13:04:10",
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
            "hash": "558225b7a057b774970ac8b5fb94236abbfbbe27a40c3ca4f3e80910db42d53b"
        },
        {
            "id": 82668,
            "external_item_id": null,
            "order_id": "31",
            "tab_id": 34213,
            "item_id": 5155,
            "item_category": "DRINKS",
            "item_name": "Croissant",
            "quantity": "1.000",
            "quantity_multiplier": "1.00",
            "item_price": "3.600",
            "original_price": "3.60",
            "cost_price": "0.00",
            "price_level": 1,
            "status": "NEW",
            "linked_to_item": null,
            "linked_to_offer": null,
            "linked_to_promotion": null,
            "course": 2,
            "current_course": 2,
            "order_msg": null,
            "ordered_by": "John Doe",
            "device_id": "EPOS Mini 1",
            "seq_number": "036-0000000357",
            "time_ordered": "2025-04-24 13:04:10",
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
            "hash": "558225b7a057b774970ac8b5fb94236abbfbbe27a40c3ca4f3e80910db42d53b"
        },
        {
            "id": 82665,
            "external_item_id": null,
            "order_id": "31",
            "tab_id": 34213,
            "item_id": 5154,
            "item_category": "DRINKS",
            "item_name": "Flat White",
            "quantity": "1.000",
            "quantity_multiplier": "1.00",
            "item_price": "3.300",
            "original_price": "3.30",
            "cost_price": "0.00",
            "price_level": 1,
            "status": "NEW",
            "linked_to_item": 210422079,
            "linked_to_offer": null,
            "linked_to_promotion": null,
            "course": 2,
            "current_course": 2,
            "order_msg": null,
            "ordered_by": "John Doe",
            "device_id": "EPOS Mini 1",
            "seq_number": "036-0000000354",
            "time_ordered": "2025-04-24 13:04:09",
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
            "hash": "3cf21a1ea9f88c64870b1fa1b2be962ab4c156dcb6d82b64e19ce8c2ce6161ef"
        }
    ]
}
```

Shows the items on a single order. The ID is constructed by concatenating the Order ID and the Tab ID as A tab can have multiple orders. One should take the `order_id` and `tab_id` and join with an underscore to create the concatenated ID.

`GET https://mysite.rposcloud.com/api/order/{orderId_tabId}`

### Attributes

Key | Description 
-------------- | --------------
`orderId_tabId` | ***int*** The concatendated ID of the Order
