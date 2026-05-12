
# Order Item

*This model accepts additional fields of type object.*

## Structure

`OrderItem`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `ProductId` | `string` | Required | - |
| `Quantity` | `int` | Required | **Constraints**: `>= 1` |
| `Price` | `double` | Required | **Constraints**: `>= 0` |
| `Description` | `string` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
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
```

