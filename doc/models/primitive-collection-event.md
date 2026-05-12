
# Primitive Collection Event

*This model accepts additional fields of type object.*

## Structure

`PrimitiveCollectionEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EventType` | [`EventType2?`](../../doc/models/event-type-2.md) | Optional | - |
| `Ids` | `List<int>` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "eventType": "primitive.variant",
  "ids": [
    77,
    78,
    79
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

