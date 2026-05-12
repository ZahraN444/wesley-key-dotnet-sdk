
# System Alert Notification Event

*This model accepts additional fields of type object.*

## Structure

`SystemAlertNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `SystemAlertNotificationEventType` | `string` | Required, Constant | **Value**: `"system.alert"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "systemAlertNotificationEventType": "system.alert",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

