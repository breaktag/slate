<a name="line-items"></a>

# Line Item Resources

All Line Items are stored in the database and are inserted via the EPOS as part of creating orders and adding items to tabs or tables

A Line Item can be a:

- **Sale Item** - such as an item of Food, Drink or Misc. 
- **Payment** - a payment made against an Order, Tab or Line Item
- **Discount** - A discount applied to an Order, Tab or Line Item
- **Promotion** - a promotion applied to an Order, Tab or Line Item
- **Voided Item** - a Sale item, Payment, Discount or Promotion that has been voided and no longer applicable

## Sale Item

A sale item represents an item of Food, Drink or Other which is sold to a customer. 

```json
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
}
```

## Payment Item

A sale item represents an payment made against an order or tab to pay for sales items.

```json
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
```

## Discount Item

A discount item represents a saving applied to an order, tab or line item.

```json
{
  "id": 82307,
  "order_id": "12",
  "tab_id": 34212,
  "item_name": "10% Staff Discount",
  "item_price": "-10.000",
  "tax_item_price": 0,
  "tax_rate": null,
  "original_price": "0",
  "status": "COMPLETE",
  "time_ordered": "2025-04-23 14:02:25",
  "ordered_by": "John Doe",
  "device_id": "EPOS Mini 1",
  "seq_number": "578-0000000006",
  "collection": null,
  "delivery": null,
  "online_order": "N",
  "discount_id": "28619ae8-269e-4ca5-a3cf-ccf7c5e8f545",
  "active": "Y",
  "hash": "185c029db4cbd996ffdb2906be351efd1bf96eee387c65642fad0baab54c7c77"
}
```

## Discount Audit Item

A discount audit item represents a saving applied to an order, tab or line item.

```json
// TBD
```

## Promotion Item

A promotion item represents a saving applied to an order usually containing multiple items or extra rules that cant be achieved with a discount.

```json
{
  "id": 82305,
  "order_id": "12",
  "tab_id": 34212,
  "item_name": "2 4 1 Guinness",
  "quantity": "1.000",
  "item_price": "-3.900",
  "total_price": -3.9,
  "tax_item_price": -3.25,
  "total_tax_price": -3.25,
  "tax_rate": "20.00",
  "tax_rate_override": "20.00",
  "original_price": "-3.900",
  "price_level": 1,
  "status": "COMPLETE",
  "linked_to_promotion": "28619ae8-269e-4ca5-a3cf-ccf7c5e8f545",
  "course": 1,
  "time_ordered": "2025-04-23 14:02:25",
  "ordered_by": "John Doe",
  "device_id": "EPOS Mini 1",
  "seq_number": "578-0000000004",
  "collection": null,
  "delivery": null,
  "online_order": "N",
  "active": "Y",
  "hash": "5af52d20287ac41fd530fd1064c12a2692d151d6711609c057d2ce917a180c94"
}
```

## Voided Item

A voided item represents a sale item, payment, discount or promotion that is no longer applicable.
Voided items are excluded from all reports, except the voids and refunds report.

```json
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
  "void_reason": '{"reason":"Spillage","voidtime":"2025-04-23 12:15:21"}',
  "void_by": "Oliver",
  "collection": null,
  "delivery": null,
  "online_order": "N",
  "discount_id": null,
  "active": "N",
  "hash": "5af52d20287ac41fd530fd1064c12a2692d151d6711609c057d2ce917a180c94"
}
```
