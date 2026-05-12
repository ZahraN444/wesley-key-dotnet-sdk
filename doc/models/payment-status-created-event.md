
# Payment Status Created Event

*This model accepts additional fields of type object.*

## Structure

`PaymentStatusCreatedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `PaymentStatusCreatedId` | `string` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "paymentStatusCreatedId": "ps_123",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

