
# System Performance Notification Event

*This model accepts additional fields of type object.*

## Structure

`SystemPerformanceNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `SystemPerformanceNotificationEventType` | `string` | Required, Constant | **Value**: `"system.performance"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "systemPerformanceNotificationEventType": "system.performance",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

