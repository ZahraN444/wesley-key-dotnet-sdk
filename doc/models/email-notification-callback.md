
# Email Notification Callback

*This model accepts additional fields of type object.*

## Structure

`EmailNotificationCallback`

## Fields

| Name | Type | Tags | Description |
|  --- | --- | --- | --- |
| `MessageId` | `string` | Optional | - |
| `RecipientEmail` | `string` | Optional | - |
| `Status` | [`Status1?`](../../doc/models/status-1.md) | Optional | - |
| `AdditionalProperties` | `object this[string key]` | Optional | - |

## Example (as JSON)

```json
{
  "messageId": "msg_001",
  "recipientEmail": "user@example.com",
  "status": "sent",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

