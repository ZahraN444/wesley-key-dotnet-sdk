
# System Maintenance Notification Event

*This model accepts additional fields of type object.*

## Structure

`SystemMaintenanceNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `SystemMaintenanceNotificationEventType` | `string` | Required, Constant | **Value**: `"system.maintenance"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "systemMaintenanceNotificationEventType": "system.maintenance",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

