
# User Status Notification Event

*This model accepts additional fields of type object.*

## Structure

`UserStatusNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `UserStatusNotificationEventType` | `string` | Required, Constant | **Value**: `"user.status"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "userStatusNotificationEventType": "user.status",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

