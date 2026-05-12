
# Create Order Request

*This model accepts additional fields of type object.*

## Structure

`CreateOrderRequest`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `CustomerId` | `string` | Required | Unique identifier for the customer |
| `Items` | [`List<OrderItem>`](../../doc/models/order-item.md) | Required | **Constraints**: *Minimum Items*: `1` |
| `CallbackUrl` | `string` | Required | URL to receive callback notifications |
| `Document` | `Stream` | Optional | Binary file upload |
| `Metadata` | `object` | Optional | Additional order metadata |
| `Attributes` | `Dictionary<string, string>` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "customerId": "cust_12345",
  "items": [
    {
      "productId": "prod_001",
      "quantity": 2,
      "price": 29.99,
      "description": "Premium Widget",
      "exampleAdditionalProperty": {
        "key1": "val1",
        "key2": "val2"
      }
    }
  ],
  "callbackUrl": "https://merchant.example.com/callbacks/payment",
  "attributes": {
    "color": "red",
    "size": "XL"
  },
  "document": "data:text/plain;name=dummy_file;base64,",
  "metadata": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

