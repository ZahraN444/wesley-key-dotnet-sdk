
# Payment Status Updated Event

*This model accepts additional fields of type object.*

## Structure

`PaymentStatusUpdatedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `PaymentStatusId` | `string` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "paymentStatusId": "ps_123",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

