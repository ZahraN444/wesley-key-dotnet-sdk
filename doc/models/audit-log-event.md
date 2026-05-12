
# Audit Log Event

*This model accepts additional fields of type object.*

## Structure

`AuditLogEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `EventType` | [`EventType3?`](../../doc/models/event-type-3.md) | Optional | - |
| `Actor` | `string` | Optional | - |
| `Action` | `string` | Optional | - |
| `Context` | `object` | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "eventType": "audit.log",
  "actor": "actor0",
  "action": "action2",
  "context": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

