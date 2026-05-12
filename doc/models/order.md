
# Order

*This model accepts additional fields of type object.*

## Structure

`Order`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `OrderId` | `string` | Optional | - |
| `CustomerId` | `string` | Optional | - |
| `Items` | [`List<OrderItem>`](../../doc/models/order-item.md) | Optional | - |
| `TotalAmount` | `double?` | Optional | - |
| `Status` | [`Status?`](../../doc/models/status.md) | Optional | - |
| `CreatedAt` | `DateTime?` | Optional | - |
| `UpdatedAt` | `DateTime?` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "orderId": "order_789",
  "customerId": "cust_12345",
  "totalAmount": 59.98,
  "status": "pending",
  "createdAt": "09/19/2025 10:30:00",
  "updatedAt": "09/19/2025 10:30:00",
  "items": [
    {
      "productId": "productId2",
      "quantity": 22,
      "price": 56.94,
      "description": "description2",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

