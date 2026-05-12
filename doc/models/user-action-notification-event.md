
# User Action Notification Event

*This model accepts additional fields of type object.*

## Structure

`UserActionNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `UserActionNotificationEventType` | `string` | Required, Constant | **Value**: `"user.action"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "userActionNotificationEventType": "user.action",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

