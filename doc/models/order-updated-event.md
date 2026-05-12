
# Order Updated Event

*This model accepts additional fields of type object.*

## Structure

`OrderUpdatedEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EventType` | [`EventType?`](../../doc/models/event-type.md) | Optional | - |
| `OrderUpdatedId` | `int` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "orderUpdatedId": 91,
  "eventType": "order.updated",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

