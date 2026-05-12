
# User Preference Notification Event

*This model accepts additional fields of type object.*

## Structure

`UserPreferenceNotificationEvent`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `UserPreferenceNotificationEventType` | `string` | Required, Constant | **Value**: `"user.preference"` |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "userPreferenceNotificationEventType": "user.preference",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

