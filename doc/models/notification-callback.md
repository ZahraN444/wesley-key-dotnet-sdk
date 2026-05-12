
# Notification Callback

*This model accepts additional fields of type object.*

## Structure

`NotificationCallback`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `NotificationType` | `string` | Required | - |
| `Subject` | `string` | Required | - |
| `Message` | `string` | Required | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "notificationType": "email",
  "subject": "Order Coonfirmation",
  "message": "msg_email_789",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

