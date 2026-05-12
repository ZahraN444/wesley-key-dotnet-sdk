
# Payment Completed Event

*This model accepts additional fields of type object.*

## Structure

`PaymentCompletedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EventType` | [`EventType1?`](../../doc/models/event-type-1.md) | Optional | - |
| `PaymentId` | `int` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "paymentId": 91,
  "eventType": "payment.completed",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

